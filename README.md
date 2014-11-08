## 1・新規ProjectをSingleViewで作成する

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


## ３・貼付けたwebviewをドラッグしてview Controllerにくっつけ、delgateを追加する

![スクリーンショット 2014-08-19 0.11.37.png](https://qiita-image-store.s3.amazonaws.com/0/15812/7e4ea95b-bb50-5f6e-dcc5-94d070d4714a.png)

## ４・webViewからCtrlを押しっぱなしでViewController.swiftにドラッグして、アウトレットを追加する。

![スクリーンショット 2014-08-19 0.12.29.png](https://qiita-image-store.s3.amazonaws.com/0/15812/f5c3cbbc-9258-8192-f351-01eba9ded2fe.png)


## ５・view Controllerを以下のように修正する。

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

  //表示したいURLを設定(初期化)
  var targetURL = "http://rakutenqute.herokuapp.com/"


  override func viewDidLoad() {
    super.viewDidLoad()
    // Do any additional setup after loading the view, typically from a nib.

    // webviewの表示を行うメソッドを呼び出す
    loadAddressURL()

  }

  override func didReceiveMemoryWarning() {
    super.didReceiveMemoryWarning()
    // Dispose of any resources that can be recreated.
  }

  func loadAddressURL(){

    // 初期化したURLを読み込む
    let requestURL = NSURL(string: targetURL)

    // 読み込んだURLの実行結果を取得する
    let req = NSURLRequest(URL:requestURL!)

    // webvieにデータをロードする
    webView.loadRequest(req)
    webView.scalesPageToFit = true

  }

}

```

## ６・指定したURLが表示されれば成功

白い画面が数秒表示されますが、慌てずに待ちましょう。


![スクリーンショット 2014-08-29 0.29.06.png](https://qiita-image-store.s3.amazonaws.com/0/15812/ceb92b55-e8a6-8ad7-db87-f9f8cb26cde5.png)


![swift_2.gif](https://qiita-image-store.s3.amazonaws.com/0/15812/a06135aa-1dcb-167e-49ec-d99ed4cffbe5.gif)



<br>
### 備考
表示しているURLは[Rakuten Qute!](http://rakutenqute.me/)というwebアプリです。

[Rakuten Qute!](http://rakutenqute.herokuapp.com/)
<br>
### ご質問
なぜかScales Page To Fitをチェックしてもサイズが調整されません。。。
swiftでwebview内のページを調整する方法をご存知の方おりましたら
コメントのほど、宜しくお願いします :smile:

### 追記
画像を更新しました！
