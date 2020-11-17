# music_app
Podcastやローカルの音楽を再生できるアプリ。
iPod的なWheelUIで再生やシークができ、倍速再生や複数同時再生などの機能を実現予定

## pubspec.yaml記載　2020/11/17現在利用中の主なPackage  　
 - [audioplayers](https://pub.dev/packages/audioplayers)
   - 音楽プレイヤーの再生機能を実現するためのPackage.複数のオーディオファイルを同時に再生できる
 - [audio_service](https://pub.dev/packages/audio_service)
   - バックグラウンド再生ができるPackage
 - [just_audio](https://pub.dev/packages/just_audio)
   - audioplayersと機能が重複しているがaudio_serviceと一緒に使えるためこちらをメインで利用する予定
 - [podcast_search](https://pub.dev/packages/podcast_search)
 - [flutter_slidable](https://pub.dev/packages/flutter_slidable)
 - [fab_circular_menu](https://pub.dev/packages/fab_circular_menu)
   - FloatingActionButtonの外周にボタンを付ける事ができるPackage
 - [file_picker](https://pub.dev/packages/file_picker)
   - ローカルのファイルパスやファイル名などの情報を取得できるPackage
 - [path_provider](https://pub.dev/packages/path_provider)
   - アプリ配下のドキュメントディレクトリのパスを取得できるPackage
 - [firebase_core](https://pub.dev/packages/firebase_core)
 - [cloud_firestore](https://pub.dev/packages/cloud_firestore)
 - [html](https://pub.dev/packages/html)
 - [lint](https://pub.dev/packages/lint)
   - 静的解析

## 遷移図
 - https://www.figma.com/file/S0Gn6fbdZEeCorPpA17LYo/Music-app?node-id=0%3A1
 
## Trello
 - https://trello.com/b/2f0qD7ci/flutter%E5%A4%A7%E5%AD%A6music-app


## 現在起きている問題・課題
- File_pickerでiOSのMusicディレクトリからパスを取得しても1度目は再生できない。（1度目でキャッシュされるため2回同じファイルを選択すると再生できる）
- iOS Simulator上でローカルの音楽ファイルが再生できないため、Androidエミュレータを使う
  またはリリースビルド `flutter run --release` で実機確認する必要がある
