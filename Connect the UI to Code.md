# Connect the UI to Code
[公式](https://developer.apple.com/library/archive/referencelibrary/GettingStarted/DevelopiOSAppsSwift/ConnectTheUIToCode.html#//apple_ref/doc/uid/TP40015214-CH22-SW1)  

## 学習目標（チュートリアルに記載されているもの）

- [ ] ストーリーボード内のシーンと基になるビューコントローラの関係を理解する
- [ ] ストーリーボード内のUI要素とソースコード間のアウトレットとアクションの接続を作成する
- [ ] テキストフィールドからユーザ入力を処理し，その結果をUIに表示する
- [ ] クラスをプロトコルに準拠させる
- [ ] 委任パターンを理解する
- [ ] アプリケーションアーキテクチャを設計するときに，ターゲットアクションパターンに従う

(翻訳機通したので若干意味がわからなくなっている)

## Wataruの学び

### UIをソースコードに接続する

#### IBOutlet

[IBOutletとIBAction：関連付けでラクラクパーツを配置しよう](http://iphone-app-program.com/newapp/iboutlet-and-ibaction/ibbas/)

パーツ自体をプログラムで定義した変数に紐づけるもの．  
→これでUIボタンをソースコードで変数として紐づけて，ソースコードで状態遷移ができる．

#### デリゲート(以下参考)

[【swift】デリゲートって何だ？出来るだけ分かりやすく解説します](http://egao.blog/programming/swift_delegate)  
[【swift】イラストで分かる！具体的なDelegateの使い方。](https://qiita.com/narukun/items/326bd50a78cf34371169)

#### デリゲートとは

プロトコルを用いてあるクラスの処理を他のクラスのインスタンスに任せるもの

例：  
UITableViewが保持しているプロトコルのUITableViewDelegateやUITableDataSourceで他のクラスを処理してもらい，UITableViewのUIを完成させる．

>> プロトコルとは？？  
>> [Swift言語を学ぶ-プロトコル-](http://tea-leaves.jp/swift/content/%E3%83%97%E3%83%AD%E3%83%88%E3%82%B3%E3%83%AB)
>> クラスの挙動を決めた設計図のようなもの.  
>> クラス自体に設計図の側面があるが，クラスが属性や挙動の細部を記述しているのに対して，プロトコルは外部へのインターフェースを定義する．

#### デリゲートの実装方法

必要な要素

1. プロトコル
2. 処理を任せるクラス
3. 処理を任されるクラス

例：（UITableViewに当てはめる）

1. プロトコル：UITableViewDelegateとUITableViewDataSource
2. 処理を任せるクラス：UITableView
3. 処理を任されるクラス：UIViewController

#### 今回のデリゲート使用例

1. プロトコル： UITextFieldDelegate
2. 処理を任せるクラス：ViewController
3. 処理を任されるクラス：UITextFeld

#### 使用方法

1. デリゲートを使用するクラスを見つける(今回の場合はViewController.swift > class ViewController: UIViewController)
2. クラスの「UIViewController」の後ろにカンマ（,)を追加して「UITextFieldDelegate」を入力する．

#### viewDidLoad()

[今更だけどiOSアプリでviewDidLoadとかviewWillAppearとかが呼ばれるタイミングをまとめてみる](http://blog.livedoor.jp/sasata299/archives/52029262.html)

viewDidLoadはインスタンス化された直後に実行される（初回の一回のみ）

具体的には...  
アプリを起動したときに画面Aが表示されるときに一番最初に実行される  
画面Bに遷移したときにも一番最初に実行される  
**ここで画面Aに戻っても実行されない**  
(多分もっと繊細な話だけどイメージ程度ではこんな感じかと思ってる)

### ここで書かれるviewDidLoadのなかみ

ViewController.swiftのviewDidLoadのなかみ

```swift
override func viewDidLoad() {
        super.viewDidLoad()

        // Handle the text field's user input through delegate callbacks.
        nameTextField.delegate = self
    }
```

ViewControllerインスタンスを読み込んだときにデリゲートを利用してnameiTextFieldプロパティを再帰させる？（なんか違う気がする)

[【Swift】デリゲートを完全攻略する](https://qiita.com/jumpyoshim/items/7667e0cc81ad91016f03)

結局デリゲートは...  
他のクラスに処理を委譲したり，**通知したり**する仕組み.(通知の概念は初登場？)

```swift
nameTextField.delegate = self
```

これを日本語翻訳すると...
UITextFieldクラスのインスタンスであるnameTextFieldのdelegateプロパティにViewControllerのインスタンスを渡している．  
になるらしい（厄介）

つまりつまり  
nameTextFieldでUITextFieldDelegateプロトコルで定義されているメソッドが実行されたらViewController(自分自身=self)に教えてくれ  
と言っているらしい？

### UITextFieldDelegateプロトコル

8つのメソッドが定義されている
今回は2つのメソッドを利用する

```swift
//MARK: UITextFieldDelegate
    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        // Hide the keyboard/.
        textField.resignFirstResponder()
        return true
    }
    func textFieldDidEndEditing(_ textField: UITextField) {
        mealNameLabel.text = textField.text
    }
```
※ここら辺もしっかり解読する