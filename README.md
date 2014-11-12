## Xcodeの各部名称
<b>イメージ図</b>
![20130225020153.png](https://qiita-image-store.s3.amazonaws.com/0/15812/6b7320f9-beb4-f161-e642-e5c40ebd6bcf.png)


1.ツールバー<br>
2.ナビゲーションエリア<br>
3.ジャンプバー<br>
4.インスペクタセレクトバー<br>
5.ナビゲーションエリア<br>
6.エディタエリア<br>
7.インスペクタペイン<br>
8.フィルターバー<br>
9.デバッグバー<br>
10.ライブラリセレクトバー<br>
11.デバッグエリア<br>
12.ライブラリペイン<br>
<br>

### 詳細は以下のリンクで確認しましょう。
(commandキーを押しながらクリックすると別タブで起動することが出来ます。)
[Xcodeの使い方](http://nanananande.helpfulness.jp/post-1219/)

## STEP１の完成イメージ

![swift_2.gif](https://qiita-image-store.s3.amazonaws.com/0/15812/a06135aa-1dcb-167e-49ec-d99ed4cffbe5.gif)


## 1・新規ProjectをSingleViewで作成します。

ここではwebViewSampleというプロジェクト名で作成しています。

![スクリーンショット 2014-08-19 0.09.13.png](https://qiita-image-store.s3.amazonaws.com/0/15812/e1d847b5-91d9-b109-b9d1-595f86addbdb.png)


![スクリーンショット 2014-08-19 0.09.46.png](https://qiita-image-store.s3.amazonaws.com/0/15812/133215d6-8b8d-9cc3-5f76-654b7df6d0d4.png)


![スクリーンショット 2014-08-19 0.10.16.png](https://qiita-image-store.s3.amazonaws.com/0/15812/d747d6bc-03d0-6d6b-d14c-54b803bf50d8.png)


## ２・Main.storyboardを選択する。そしてユーティリティエリアからwebviewを選び、viewControllerへwebviewを貼付ける。そしてauto layautoを設定する。

![スクリーンショット 2014-08-19 0.11.03.png](https://qiita-image-store.s3.amazonaws.com/0/15812/a6e585a1-2c7e-cc9f-4fe7-fdce62414ada.png)

次に画面表示の最適化を行うためにauto layautoを設定していきます。
画面にぴったり合わせます。
そしてMain.storyboardの右下の「△」を押し、「Add Missing Constraints」を押して、
設定していきます。

![スクリーンショット 2014-10-29 20.53.04.png](https://qiita-image-store.s3.amazonaws.com/0/15812/68735839-f81f-9939-7543-f7d10402be38.png)

![スクリーンショット 2014-10-29 20.53.25.png](https://qiita-image-store.s3.amazonaws.com/0/15812/d32eacb4-f11e-1a29-5941-db4a34c58a34.png)


## ３・貼付けたwebviewをドラッグしてview Controllerにくっつけ、delgateを追加します。

![スクリーンショット 2014-08-19 0.11.37.png](https://qiita-image-store.s3.amazonaws.com/0/15812/7e4ea95b-bb50-5f6e-dcc5-94d070d4714a.png)

## ４・webViewからCtrlを押しっぱなしでViewController.swiftにドラッグして、アウトレットを追加します。
ここではwebViewという名前で設定しています。

![スクリーンショット 2014-08-19 0.12.29.png](https://qiita-image-store.s3.amazonaws.com/0/15812/f5c3cbbc-9258-8192-f351-01eba9ded2fe.png)


## ５・view Controllerを以下のように修正します。

```swift
//
//  ViewController.swift
//  webViewSample
//
//  Created by g08m11 on 2014/08/19.
//  Copyright (c) 2014年 Bloc. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

  @IBOutlet var webView: UIWebView!

  // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
  //表示したいURLを設定(初期化)
  var targetURL = "http://rakutenqute.herokuapp.com/"
  // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

  override func viewDidLoad() {
    super.viewDidLoad()
    // Do any additional setup after loading the view, typically from a nib.

    // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
    // webViewを表示するためのメソッド呼び出し
    loadAddressURL()
    // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

  }

  override func didReceiveMemoryWarning() {
    super.didReceiveMemoryWarning()
    // Dispose of any resources that can be recreated.
  }

  // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
  func loadAddressURL(){

    // 初期化済みのURLを読み込む
    let requestURL = NSURL(string: targetURL)

    // 読み込んだURLの実行結果を取得する
    let req = NSURLRequest(URL:requestURL!)

    // webvieにデータをロードする
    webView.loadRequest(req)
    webView.scalesPageToFit = true

  }
  // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

}

```
## ６・バグがないかチェックしましょう。
commandキー + Bを押してみましょう。
バグが無ければ以下の画像が表示されます。

![スクリーンショット 2014-11-11 21.09.17.png](https://qiita-image-store.s3.amazonaws.com/0/15812/05c948c7-c658-d597-9999-137416a29123.png)

ただ、エラーがあった場合は以下の画像が表示されます。

![スクリーンショット 2014-11-11 21.12.46.png](https://qiita-image-store.s3.amazonaws.com/0/15812/97504c02-255e-020e-2320-597de62f6e66.png)

バグが無い状態を確認した後、
commandキー + Rを押しみましょう。
自動的にiPhoneシュミレーターが起動されます。


## ７・指定したURLが表示されれば成功

白い画面が数秒表示されますが、慌てずに待ちましょう。


![スクリーンショット 2014-08-29 0.29.06.png](https://qiita-image-store.s3.amazonaws.com/0/15812/ceb92b55-e8a6-8ad7-db87-f9f8cb26cde5.png)


<br>
### 備考
表示しているURLは[Rakuten Qute!](http://rakutenqute.herokuapp.com/)というwebアプリです。

[Rakuten Qute!](http://rakutenqute.herokuapp.com/)

<br>
<br>
<br>
<br>

## STEP２の完成イメージ
(こちらはステップ１が前提となっています。)

![schooSample.gif](https://qiita-image-store.s3.amazonaws.com/0/15812/07b19c7e-c300-0350-bfc2-e0386c685b12.gif)


## 1・「webViewSample」プロジェクトを開きます。


## ２・view Controllerを以下のように修正します。

```swift
//
//  ViewController.swift
//  webViewSample
//
//  Created by g08m11 on 2014/08/19.
//  Copyright (c) 2014年 Bloc. All rights reserved.
//

import UIKit
// ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
// twitterなどのSocialへ投稿する際に必要な機能を外部から読み込むための初期化
import Social
// ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ


class ViewController: UIViewController {

  @IBOutlet var webView: UIWebView!

  //表示したいURLを設定(初期化)
  var targetURL = "http://rakutenqute.herokuapp.com/"

  // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
  // twitter投稿画面を生成するための初期化
  var myComposeView : SLComposeViewController!
  // twitter用のボタンを生成するための初期化
  var myTwitterButton: UIButton!
  // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

  override func viewDidLoad() {
    super.viewDidLoad()
    // Do any additional setup after loading the view, typically from a nib.

    // webViewを表示するためのメソッド呼び出し
    loadAddressURL()

    // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
    // twitterに似た色合いをコードで生成するための設定。色味のみの設定
    let hex: Int = 0x55ACEE
    let red = Double((hex & 0xFF0000) >> 16) / 255.0
    let green = Double((hex & 0xFF00) >> 8) / 255.0
    let blue = Double((hex & 0xFF)) / 255.0
    var myColor: UIColor = UIColor( red: CGFloat(red), green: CGFloat(green), blue: CGFloat(blue), alpha: CGFloat(1.0))
    // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ


    // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
    // twitter用のボタンを設定。ボタンを押された後にtwitter投稿用のメソッド呼び出しまで設定
    myTwitterButton = UIButton()
    myTwitterButton.frame = CGRectMake(0,0,100,100)
    myTwitterButton.backgroundColor = myColor
    myTwitterButton.layer.masksToBounds = true
    myTwitterButton.setTitle("Twitter", forState: UIControlState.Normal)
    myTwitterButton.titleLabel?.font = UIFont.systemFontOfSize(CGFloat(30))
    myTwitterButton.setTitleColor(UIColor.whiteColor(), forState: UIControlState.Normal)
    myTwitterButton.layer.cornerRadius = 50.0
    myTwitterButton.layer.position = CGPoint(x: self.view.frame.width - 55, y:self.view.frame.height - 115)
    myTwitterButton.tag = 1
    myTwitterButton.addTarget(self, action: "onPostToTwitter:", forControlEvents: .TouchUpInside)
    // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

    // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
    // twitter用のボタンを画面に表示させるための設定
    self.view.addSubview(myTwitterButton)
    // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

  }

  override func didReceiveMemoryWarning() {
    super.didReceiveMemoryWarning()
    // Dispose of any resources that can be recreated.
  }

  func loadAddressURL(){

    // 初期化済みのURLを読み込む
    let requestURL = NSURL(string: targetURL)

    // 読み込んだURLの実行結果を取得する
    let req = NSURLRequest(URL:requestURL!)

    // webvieにデータをロードする
    webView.loadRequest(req)
    webView.scalesPageToFit = true

  }

  // ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓ この部分をコピペ
  func onPostToTwitter(sender : AnyObject) {
    myComposeView = SLComposeViewController(forServiceType: SLServiceTypeTwitter)
    myComposeView.setInitialText("Schooの授業でアプリ作ったよ！  #SwiftGirls")
    self.presentViewController(myComposeView, animated: true, completion: nil)
  }
  // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑　この部分をコピペ

}

```

## ３・twitterのボタンが表示されれば成功
動作にも問題が無いかtwitterボタンを押してみましょう。

![スクリーンショット 2014-11-08 12.28.44.png](https://qiita-image-store.s3.amazonaws.com/0/15812/6e2035b4-cba7-a97c-e380-19cb7ed9f293.png)


