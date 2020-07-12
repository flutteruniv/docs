# 開発の流れ（エンジニア向け）
## issueの作成方法
1. Issuesタブをクリックする

1. issueテンプレートの[各種運用ルール](https://github.com/kboy-salon/salon_app_doc/blob/master/explanation/issues.md)を確認する

1. 自分の投稿目的に合ったissueテンプレートの「Get started」を選択して、issueを作成する
   
   ※ 「Open a blunck issue」からはissueを作成しない
   
   ※ 自分の目的に合ったissueテンプレートがない場合は担当スクラムマスターに相談する

<img width="767" alt="Issueテンプレート_20200712" src="https://user-images.githubusercontent.com/55462291/87241108-b8844b80-c45a-11ea-9999-0b37ea89a055.png">

## labelsの運用方法
- issue には以下の画像ような label を設定する事ができる
- 基本的な label は issueテンプレートから issue を作成した時に自動で設定される
- エンジニアは label を自分で変更する事はないが、issue の検索を行う時に役立つので、それぞれの label の意味は理解しておく
- 以下の label は、task issue の状況が変わった時に担当スクラムマスターが設定変更を行う
  * 3 : エンジニア募集 - raise your hand
  * 4 : 初心者大歓迎 - good first issue
  * 8 : 保留 - wontfix
  * 9 : 実現不可能 - invalid
  * 10 : 重複 - duplicate
<img width="620" alt="labels一覧_20200712" src="https://user-images.githubusercontent.com/55462291/87243229-4d913f80-c46f-11ea-861e-57d8aa7bea44.png">

## GitHubの運用ルール([GitHub Flow](https://tracpath.com/bootcamp/learning_git_github_flow.html)と呼ばれる運用フローを採用)
以下の4つを準拠して、masterブランチは常にリリース可能な状態にしながら、GitHubを運用する

1. 新しい作業を開始する際は、必ず、最新のmasterブランチから作業ブランチを切る

1. 作業ブランチは定期的にプッシュする

1. 作業が完了したら、プルリクエストを使って、プロダクトオーナーや担当スクラムマスターにコードレビューを依頼する

1. コードレビューを通過したら、速やかに、プロダクトオーナーにmasterブランチのマージを依頼する

## 各ブランチの役割と命名規則
### masterブランチ
- リリース可能な状態だけを管理する

- 特定のブランチからマージすることによってしか更新されない

- 直接コミットしてはならないという制約を持つ

- [バージョン毎のtag](https://docs.github.com/ja/github/administering-a-repository/viewing-your-repositorys-releases-and-tags)はここから生まれる

### featureブランチ
- 機能追加・改修などを行う作業ブランチ

- masterブランチから、featureブランチを切る

- レビュー完了後はmasterブランチにマージされ、featureブランチはMergedのまま保持される

- featureブランチは以下のように「feature/(変更の種類)_(作業内容の簡単な説明)」のような命名規則でブランチを切る

  * 命名例１ ： feature/add_buttom_on_login_screen

  * 命名例２ ： feature/change_date_picker_on_event_screen

  * 命名例３ ： feature/delete_good_buttom_on_video_screen

  * 命名例４ ： feature/update_layout_on_withdrawal_screen

## プルリクの作成方法（→大まかな流れは[GitHubのDocs](https://docs.github.com/ja/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)を確認)
1. 自分が担当している開発が完了したら、作業ブランチにプルする

1. Pull requestsタブをクリックする

1. New pull request をクリックする

1. compare を作業ブランチに設定し、base を master に設定する

1. 画面上部に表示される[ガイドライン](https://github.com/kboy-salon/salon_app/blob/master/.github/CONTRIBUTING.md)に沿って必要事項を入力する

1. Create pull request をクリックする
