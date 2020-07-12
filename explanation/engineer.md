# 開発の流れ（エンジニア向け）
### issueの作成方法
1. Issuesタブをクリックする
2. issueテンプレートの[各種運用ルール](https://github.com/kboy-salon/salon_app_doc/blob/master/explanation/issues.md)を確認する
3. 自分の投稿目的に合ったissueテンプレートの「Get started」を選択して、issueを作成する
   
   ※ 「Open a blunck issue」からはissueを作成しない
   
   ※ 自分の目的に合ったissueテンプレートがない場合はスクラムマスターに相談する

<img width="767" alt="Issueテンプレート_20200712" src="https://user-images.githubusercontent.com/55462291/87241108-b8844b80-c45a-11ea-9999-0b37ea89a055.png">


### GitHubFlowの運用ルール、ブランチの命名規則
以下のQiitaを参考に抜粋をまとめる（山村）
※プルリクエストにWork In Progressのルールも用意する？
※ブランチはmaster ← develop ← feature の 構成を想定
https://tracpath.com/bootcamp/learning_git_github_flow.html
https://qiita.com/tbpgr/items/4ff76ef35c4ff0ec8314
https://qiita.com/katsunory/items/252c5fd2f70480af9bbb

### プルリクのテンプレート
以下のQiitaを参考に抜粋をまとめる（山村）
https://qiita.com/nyamogera/items/3fe6985b45fbd5377184

## すささんのメモ（以下、あとで削除）
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

