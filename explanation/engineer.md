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

### プルリクの作成方法（→大まかな流れは[GitHubのDocs](https://docs.github.com/ja/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)を確認)
1. 自分が担当している開発が完了したら、作業ブランチにプルする
2. Pull requestsタブをクリックする
3. New pull request をクリックする
4. compare を作業ブランチに設定し、base を master に設定する
5. 画面上部に表示される[ガイドライン](https://github.com/kboy-salon/salon_app/blob/master/.github/CONTRIBUTING.md)に沿って必要事項を入力する
6. Create pull request をクリックする
