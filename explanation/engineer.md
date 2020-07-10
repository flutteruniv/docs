# 開発の流れ（エンジニア向け）

ここに開発の流れ（エンジニア向け）を書く。

## メモ（以下、あとで削除してください）

### Github flow

* Github flow をそのまま採用でよいとおもう（git flow ではない）
* https://tracpath.com/bootcamp/learning_git_github_flow.html のサイトがよくまとまっています。リンク張って読んでもらうでもいいかも。

### Issue ルール

* ストーリー issue
  * Label は story
  * 必ず Projects に紐付ける
  * 必ず担当者をアサインする
  * タスクを作ったら、説明欄にタスク issue の番号を記載する
    * Github issue には issue の親子を設定する機能が無いため運用でカバー
  * closeできるのはプロダクトオーナー

* タスク issue
  * Label は task
  * Projects に紐付けない
  * タスクを作ったら、説明欄にストーリー issue の番号を記載する
    * Github issue には issue の親子を設定する機能が無いため運用でカバー
  * closeできるのはスクラムマスター
  
