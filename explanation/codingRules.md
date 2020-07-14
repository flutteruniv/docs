# コード規約
## 目的
- 可読性向上  
- 保守性向上  
- 品質向上

## 原則

- 記述方法に悩んだらFlutter大学動画の方式に合わせる。
- Format on save設定を有効にしdartfmtを適用させる。


## 詳細  
(DO 厳守、DON’T 厳禁、PREFER 推奨、AVOID 非推奨、CONSIDER 適宜適切に)

- ### DO: クラス名は大文字開始のupper camel case

例)  
```dart:sample.dart
class BookListModel
```  


- ### DO: 変数、定数、メソッドは小文字開始のlower camel case  

例)  
```dart:sample.dart
void changeKboyText() {
    		kboyText = 'kboyさんかっこいい！！！';
    		notifyListeners();
}
```


- ### DO: ファイル名はスネークケースであり、pageなのかmodelなのかを明示する  

例)  
```dart:sample.dart
signup_page.dart  
signup_model.dart
```

- ### DO: ディレクトリはdomain, presentationのように分け、画面ごとにadd_book、book_list、signupのように分ける  

例)  
![alt](https://github.com/RN24Nishioka/pictures-public/blob/master/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202020-07-07%209.15.55.png?raw=true)


- ### DO: providerモデルを用いて実装する(stateful widget使わない)

- ### DO: スペース、タブ、改行の細かい仕様はdartfmtに従う。IDEの自動フォーマット機能で簡単に自動採用できる。  
この機能を用いることでdartfmtが働き下記gitに記載あるルールでで整形される。  
https://github.com/dart-lang/dart_style/wiki/Formatting-Rules  

#### 設定方法↓  
```
Preference(or Setting)  
→Language & Frameworks  
→Flutter  
→Format code on saveをチェック☑  
(右クリック→Reformat Code with dartfmtでも整形自体は可能。)
```
↓ここにも記載あります↓  
https://github.com/kboy-salon/questions/issues/32#issuecomment-642411563


- ### DO: ライブラリをインポートする際は、dependenciesのバージョンを記載する  
例)   
```dart:sample.dart
  cupertino_icons: ^0.1.3
  firebase_core: ^0.4.5  
  provider: ^4.1.3
  cloud_firestore: ^0.13.7
  intl: ^0.16.1
  flutter_google_places: ^0.2.5
  google_maps_webservice: ^0.0.17
  firebase_auth: ^0.16.1
  keyboard_actions: ^3.2.1+1
  firebase_storage: ^3.1.6
  uuid: ^2.1.0
  image_picker: ^0.6.7+2
  auto_size_text: ^2.1.0
```

- ### PREFER: dartfmtが適応されやすいコードを心がける
https://dart.dev/guides/language/effective-dart/style#formatting

- ### PREFER: Automatically formatted code with trailing commasを使用する  
(コンマを使用すれば自動的に反映されるのでFormat code on save以外に特別な設定は不要。)  
![alt](https://github.com/RN24Nishioka/pictures-public/blob/master/unnamed.png?raw=true)
https://flutter.dev/docs/development/tools/formatting


- ### PREFER: 変数を宣言するときは、型を明示的に指定する  
例)  
```dart:sample.dart
  String mail;
  String password';
 ```

- ### AVOID: 三項演算子は長くなりすぎないようにする  
例)  
```dart:sample.dart
// OK
color: android ? Colors.white : Colors.red,
// NG
color: android ? new Text(...) : new Text(...),
```

- ### AVOID: 余分なコードは減らす  
例) newの使用  


- ### AVOID: マジックナンバーやマジックストリングなどハードコーディングは避ける  
避けれない場合は、他の実装者にも伝わるようにコメントを記載する  
例)  
[マジックナンバーにとは？（Wikipedia）](https://ja.wikipedia.org/wiki/%E3%83%9E%E3%82%B8%E3%83%83%E3%82%AF%E3%83%8A%E3%83%B3%E3%83%90%E3%83%BC_(%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0))

- ### DON’T: Android studio以外 を使う

- ### CONSIDER: その他ここに記載のないことは適宜適切に！
