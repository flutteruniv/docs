# CodeBoy2について

Flutter大学内のメンバー同士で、「1時間〇〇円で指導します」のような商品を売買することができます。その機能をCodeBoy2と呼んでいます。

## 決済方法
- 決済方法は2種類あります。日本円でのクレジットカード決済と、Flutter大学専用コインのFUTでの決済です。
- FUT決済には手数料はかかりません。
- クレジットカード決済には手数料がかかります。手数料はコミュニティへの貢献度によって変動します。後述します。

## 手数料
- 現在あなたが講師としてメンタープランを売った場合の手数料は、https://flutteruniv.com/teacher にて確認できます。
- コミュニティに最も貢献している人は決済手数料込みで4%しか手数料がかかりません。(stripe手数料3.6%、Flutter大学のプラットフォーム取り分0.4%)

<img width="500" alt="CleanShot 2023-06-23 at 19 56 01@2x" src="https://github.com/flutteruniv/docs/assets/17683316/a93c0685-f4e2-4dd0-a953-4bd7937eb3e5">

### 手数料決定のロジック

#### 講師のコミュニティへの貢献度で手数料を決定する
- あまり貢献していない -> 10%
- たまに貢献している   -> 8%
- 貢献している         -> 6%
- とても貢献している   -> 4%

#### 貢献度の決定方法
- 直近3ヶ月での総流通量を貢献した人数(FUTをもらった人数)で割ることで
- 一人あたりの平均獲得FUTが出る
- それを基準としてあまり貢献していない、とても貢献している人のFUT量を計算している

ちなみにロジックのコードは[ここ](https://github.com/flutteruniv/salon_functions/blob/develop/functions/src/teacher_commission.ts)に書かれています。

## メンタープランの販売方法
1. [講師ページ](https://flutteruniv.com/teacher)で本人確認を完了する
2. [講師ページ](https://flutteruniv.com/teacher)から「プレビュー」ボタンを押し、自分のページを表示する（[例：kboyのページ](https://flutteruniv.com/users/DKujPNcD0nSfr7adnhi6waBkrtS2)）
3. 自分のページのプラン一覧下のボタンからプラン追加ボタンを押す

## さらにCodeBoy2開発への思いを知りたい方はこちら
https://zenn.dev/flutteruniv_dev/articles/e0fb6bcd593584
