# Build a Basic UI

[公式](https://developer.apple.com/library/archive/referencelibrary/GettingStarted/DevelopiOSAppsSwift/BuildABasicUI.html#//apple_ref/doc/uid/TP40015214-CH5-SW1)

## 学習目標（チュートリアルに記載されているもの）

- [x] Xcodeでプロジェクトを作成する
- [x] Xcodeプロジェクトテンプレートで作成されたキーファイルの目的を特定する
- [x] プロジェクト内のファイルを開いて切り替える
- [x] iOS Simulatorでアプリを起動する
- [x] ストーリーボードのUI要素の追加，移動，サイズ変更
- [x] ストーリーボードのUI要素の属性を属性インスペクタを利用して編集する
- [x] アウトラインビューを使用してUI要素を表示および再配置する
- [x] アシスタントエディタのプレビューモードを使用してストーリーボードのUIをプレビューする
- [x] 自動レイアウトを使用して，ユーザのデバイスサイズに自動的に適応するUIをレイアウトする

## Wataruの学び

### iOSシミュレータ

Command-Rを押すことで起動可能

### XCodeのプロジェクトファイルの構成

#### AppDelegate.swift  

[参考サイト①](https://qiita.com/SoyaTakahashi/items/cc8f48af792c353cd9f3)  
[参考サイト②-はじめてのSwiftアプリ制作1: プロジェクトの作り方-](https://qiita.com/tsubamechi/items/dfdff846ac574297a0e2)

プロジェクト>プロジェクトフォルダ>AppDelegate.swift

##### 主要な機能

アプリ全体のライフタイムイベントを管理するクラス

>**ライフタイムイベント**  
>起動, バックグラウンド, フォアグラウンド, 終了時, etc の状態遷移

#### ViewController.swift

[参考①-SwiftでViewControllerを使う-](https://qiita.com/h_nagami/items/66dc637463f98716bfa5)  
[参考②-iOS アプリの構造がどのようになっているか紐解いてみる-](http://glassonion.hatenablog.com/entry/20120507/1336320038)

UIViewControllerクラスを継承したクラス.  
１画面ごとに作成される．  
UI部品のアクション（例えばボタンを押したときの動き）を定義したり，複数のUI部品が連携したときの動きを定義する．

>**ViewController**  
>Viewを管理・操作（表示・非表示・配置・アニメーションなど）をするクラスの一つ  
>一番よく使うクラスとしてUIViewControllerがある．

#### Main.storyboard
