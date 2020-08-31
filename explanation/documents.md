# ドキュメント類

## 設計

### アーキテクチャ

* Flutter大学と同様、Providerのpackageを入れる
* 基本的には１画面につきpageとmodelがあるイメージ

### 画面遷移

https://drive.google.com/file/d/1rv-XQ3gziEC0AYWx5yOH8lupE909W-7e/view

### FireStore ER図

随時更新中  

https://cacoo.com/diagrams/5OdCscHjK0xRslbu/5135D

### 3rd party アカウント

3rd party|内容
--|--
GitHub|KBOYさんに問合せればAPI用のアクセストークンが取得できます
Slack|不明なのでKBOYさんに問合せしてください
Stripe|KBOYさんに問合せれば開発用アカウントが取得できます
Vimeo|KBOYさんに問合せればストリーミングURLやAPIキーが取得できます
Firebase|KBOYさんやスクラムマスターに問合せれば招待してくれます


### コーディング規約

#### 原則

- 記述方法に悩んだらFlutter大学動画の方式に合わせる。
- Format on save設定を有効にしdartfmtを適用させる。

#### 詳細  
詳細は[ここ](https://github.com/kboy-salon/salon_app_doc/blob/master/explanation/codingRules.md)に記載してあるのでざっと目を通してください。

## 事前準備
### 入会登録

- サロンアプリの動作確認や実装を行う上で、事前に入会Webで入会登録および課金が完了しておく必要があります。
- 以下の手順で、入会登録および課金まで完了することができます。

1. （既に Firebase Auth のメールアドレスを登録していた場合）[Firebase コンソールのAuthentication](https://console.firebase.google.com/u/1/project/kboy-salon-app/authentication/users)で自分のメールアドレスを削除する
2. [入会Web](https://kboy-salon-app.web.app/#/)を開く
3. 入会登録画面でメールアドレスとパスワードを入力し、「決済画面へ」ボタンを押下
4. Stripeの決済画面で、以下のテスト用クレジットカード番号、有効期限、CVCを入力して、申し込みをする
- クレジットカード番号: 4242424242424242 ([テスト用クレジットカード番号](https://stripe.com/docs/testing#cards) 参照)
- 有効期限: 12/22 (未来ならいつでもよい）
- CVC: 222 (なんでもよい）

