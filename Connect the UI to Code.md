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
1. 処理を任せるクラス
1. 処理を任されるクラス

例：（UITableViewに当てはめる）

1. プロトコル：UITableViewDelegateとUITableViewDataSource
2. 処理を任せるクラス：UITableView
3. 処理を任されるクラス：UIViewController

#### 今回のデリゲート使用例

1. プロトコル： UITextFieldDelegate
2. 処理を任せるクラス：UIViewController??
3. 処理を任されるクラス：???

#### 使用方法

1. デリゲートを使用するクラスを見つける(今回の場合はViewController.swift > class ViewController: UIViewController)
2. クラスの「UIViewController」の後ろにカンマ（,)を追加して「UITextFieldDelegate」を入力する．


#### viewDidLoad

次回はここら辺から（チュートリアルとしては「ViewControllerオブジェクトをnameTextFieldプロパティのデリゲートとして設定する」ところから
）