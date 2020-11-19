# salon_admin_web

- サロンアプリの管理Webアプリ
- Flutter Web で作ってます

ログインとログアウト
--
![login](https://user-images.githubusercontent.com/13707135/99695844-653d9c00-2ad1-11eb-8e5b-bbd4846c4bbd.gif)

ダッシュボード／レスポンシブ対応
--
![responsive](https://user-images.githubusercontent.com/13707135/99696244-d54c2200-2ad1-11eb-9ebd-c6bb6f8fb099.gif)

メンバー一覧、詳細
--
![member](https://user-images.githubusercontent.com/13707135/99696204-c8c7c980-2ad1-11eb-9107-96fc1edf436c.gif)


お知らせ一覧、作成、編集
--
![notice](https://user-images.githubusercontent.com/13707135/99695972-88684b80-2ad1-11eb-849a-167a49c98faa.gif)

# ソースコードの解説

## フォルダ構成

フォルダ名|説明
--|--
config|設定まわり。mainから呼ばれる`App`もここに含まれる。
domain|データ構造。Entityとも呼ぶ。
exception|例外クラスの集合体。
extension|拡張クラスの集合体。
presentation|StatelessWidgetのページ（View）と、ChangeNotifier（ViewModel）のセットの集合体。
repository|データの取得や操作を担う。

## 使用しているパッケージの補足

パッケージ名|補足
--|--
[charts_flutter](https://pub.dev/packages/charts_flutter)|グラフ描画
[flutter_admin_scaffold](https://pub.dev/packages/flutter_admin_scaffold)| サイドバーをつけて管理画面っぽくするやつ。サロンメンバーの[すさ](https://github.com/susatthi)作成。
[flutter_bootstrap](https://pub.dev/packages/flutter_bootstrap)|Bootstrapのcontainer（col-md-4とか）が使える。
[flutter_bootstrap_widgets](https://pub.dev/packages/flutter_bootstrap_widgets)| Bootstrap3風にしてくれる、管理WebをWebっぽくするためにいたるところで使ってます。サロンメンバーの[すさ](https://github.com/susatthi)作成。
[flutter_web_data_table](https://pub.dev/packages/flutter_web_data_table)| テーブルをもっと簡単に使えるようにする、一覧画面で使ってます。サロンメンバーの[すさ](https://github.com/susatthi)作成。
[flutter_web_router](https://pub.dev/packages/flutter_web_router)| ルーティングを簡単に使えるようにする、`/items/view/{itemId}`みたいにワイルドカードをあつかえます。サロンメンバーの[すさ](https://github.com/susatthi)作成。

## アーキテクチャ

- MVVM + Repository

![アーキテクチャ](https://user-images.githubusercontent.com/13707135/99692751-fb6fc300-2acd-11eb-895a-da3bacfc63b2.png)

- 詳細

![アーキテクチャ詳細](https://user-images.githubusercontent.com/13707135/99694388-b77dbd80-2acf-11eb-8697-ce6d258a8d93.png)

### 【解説】 BaseModel extends ChangeNotifier

- ViewModelに相当する部分のうち、共通処理をあつめた`BaseModel`を作り、各ページのViewModelは`BaseModel`を継承しています。
- BaseModelが担う共通処理
  - ローディングのフラグ管理
  - リクエスト情報の保持
  - 各種ダイアログの表示
  - 画面遷移処理
  - セッション管理
- `context`依存問題
  - `BaseModel`のコンストラクターは`context`を引数にとります。
  -  ViewModelが`context`を持つことで画面遷移とポップアップ表示のトリガーをViewModelが担うことが出来て、View側にロジックを一切書かなくすることが出来る。
  - 本来は、ViewModelのViewへの依存性を低くし、ViewModelの単体テストを容易にできるようにすることが望ましい。
  - そのためにはViewModelは`context`は持たない方がよいが、実装の難易度が上がってしまうので現状のままとしている。
  - ViewModelの`context`非依存のアイデアとしては、streamやlistener等を使ってViewModelからViewにイベントを発行し、View側で画面遷移とポップアップ表示をすることが考えられる。

### 【解説】 ルーティング

- ルーティングの細かい実装は [flutter_web_router](https://pub.dev/packages/flutter_web_router) packageに閉じ込めました。ここではルーティングの考え方を説明します。
- Flutter Web では、事前に名前付きパスを定義して、`Navigator.of(context).pushNamed('/dashboard');`のようにパスを与えて画面遷移します。
- 普通に`MaterialApp().routes` で各画面のパスを固定で定義し、例えばお知らせ詳細画面を開くときにお知らせ情報（`Notice`）をコンストラクターで与えて表示すると、ブラウザ再読込したときにお知らせ情報が無くなって正しく表示されない問題が起きます。
- この問題を解決するために、お知らせ詳細画面を表示する場合は `/notices/view/{noticeId}`、お知らせ編集画面を表示する場合は`/notices/edit/{noticeId}`のように、パスに`noticeId`を含めてしまえばブラウザ再読込みされても同じ画面を表示できます。
- [flutter_web_router](https://pub.dev/packages/flutter_web_router) を使って以下のような処理を行っています。
  - `MaterialApp().onGenerateRoute` でパスを定義する際は、`/notices/view/{noticeId}`のようにワイルドカード付きで定義しておく
  - 画面遷移するときは`/notices/view/{noticeId}`に合致するように、例えば`/notices/view/ZU47spXSBzU2ZGnVOlAm`のようなパスを生成してpushする
  - `MaterialApp().onGenerateRoute`でリクエストされたパスを解決する際、`/notices/view/ZU47spXSBzU2ZGnVOlAm`は`/notices/view/{noticeId}`に合致すると判断し、適切な画面を呼び出す。その際
`noticeId=ZU47spXSBzU2ZGnVOlAm`という情報も画面に引き渡す。
  - 画面表示する際、お知らせ情報を取得してきて表示する。
  
### 【解説】 ログイン状態の管理

- Flutter Web では、画面表時直後に限り、ログイン中であっても `FirebaseAuth.instance.currentUser`が`NULL`を返すケースが存在します。
- これを解決するために、画面表時直後に強制的にユーザのログイン状態が確定するまで待つ処理を挟んでいます。

main.dart

```dart
Future main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // ユーザのログイン状態が確定するまで待つ
  await Firebase.initializeApp();
  await firebase.auth(firebase.app()).onAuthStateChanged.first;

  runApp(AdminApp());
}
```
- 未ログインならログイン画面へ、ログイン済みならダッシュボード画面へ遷移する制御は[flutter_web_router](https://pub.dev/packages/flutter_web_router) を使って以下のような処理を行っています。
  - `WebRouter().addFilter()` で、リクエストが来たときにログイン状態に応じた処理を追加する
    - 未ログインならログイン画面にリダイレクトする
    - ログイン済みならリクエスト通りの処理をする
    - 具体的には、 `config/router_factory.dart` の `LoginVerificationFilter` を参照ください。


