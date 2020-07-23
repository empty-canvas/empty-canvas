# Chapters

## Chapter 8: 2020-07-23

author: @maehara

### javascriptのリファクタリング

- 今回の問題点
    - エラーにならずに漏れてしまう部分がある
        - 必須となっていなく、空白とかでsubmitできてしまう
    - エラーの種類
        - 文字数やemail形式のエラーしか表示されない（この項目は必須ですというエラーなどが表示されない）
    - name,email,contentそれぞれに対して「addEventListener」をやっている（ここの部分は次回やる）

- エラーにならずに漏れてしまう部分
    - 項目に値が入力されているかのチェックをする関数の作成
        - 下記の①の場合はtureを、②の場合はfalseを返す関数
            - ①→value:'(文字列,数値でも可)'、、、など
            - ②→value:'',value:null,value:undefined、、、など
        - function required(value){}という関数を定義した
            - if(required(value) !== ''){}という形でfalseになるのを「if文」で書いていくのもあり
                - この時、「else if」という様につなげていかない（補足で説明）
            - if文を書かないで「return !!value」でチェックして、tureやfalseを返すことが可能
                - 「!!value」で終わることについては、自分で調べる
    - チェックを通過した値に対して、文字数のエラーチェックをさせるので、文字数チェックの関数の作成
        - name,contentのどちらでも利用できる関数を作成
            - function length(value,第一引数,第二引数,,,){}という値とは別に引数を渡せる様に作成
        - function length(value,min,max){return min <= value.length && value.length <= max;}としてあげる
            - nameだと30文字以内という制限なので、function length(value,0,30)としてあげると簡単に制限がかけれる
    - emailの正規表現と合致しているかのチェックする関数の作成
        - function emailCheck(value) {return regexp.test(value);}という感じで、入力値（value）をtest()メソッドでregexpと比較
        - regexpは正規表現を格納した定数
    - 上記３つの関数を利用して、チェックをする

- エラーの種類について
    - 次回までにエラーパターンを作成しておく
        - この項目は必須ですや文字数は〇〇ですなど

#### 補足
- なぜif文で「else if」をやらないのか
    - if文を見にいく時に、この時はどうするのかだけを見にいく。つまり、こうならばこれ。これならこれ。というのをわかりやすくするため。
    - これもチームで開発したり、後から修正していく時に、条件を理解するのにとても面倒になってしまう
        - コードは常に見やすい、わかりやすいを意識
    - if(条件式){条件式がture or falseなら実行する処理＋returnで処理完了}
        - 複数の場合は、さらにその下にif(条件式){条件式がture or falseなら実行する処理＋returnで処理完了}を追加していく
        - 特徴：if文が多くあっても、上から処理が始まり、一番目のif文でチェックが入り、それに該当しなかった場合は、二番目のif文でチェックが入りという感じで進んでいく。

### スコープについて（ここに書いた内容ちょっと間違っているかもw）
- １つ関数内で関数名などを定義することはできない
- 関数内で定義した関数などを他の部分で利用することはできない
- 利用する場合は、無名関数を利用することで、定義できる様になる

### AI
- javascriptの理解
    - 関数
    - オブジェクト
    - スコープの範囲
- その他
    - エラーパターンを作成しておく

### 備考
- 利用したブランチ
`feature/20200723`

- 本日のPR
https://github.com/empty-canvas/maehara-portfolio/pull/10

## Chapter 7: 2020-07-16

author: @maehara

### スタイルの継承について

- @extendの説明
    - $item:null;の役割
        - 変数$itemを定義。空では定義できないので、nullを入れてあげる
        - #{item}でスタイルを継承したいクラス内で@extendで指定

### javascriptでお問い合わせフォームの値を取得
Driver:maehara
Mob:グッチー

- formの値を取得する
    - documentオブジェクトを利用
        - querySelector('CSSセレクタ')メソッドを利用した要素の取得
        - addEventListener('イベント種類',アロー関数)でイベントが起こったときに、処理したい内容のセット
            - イベント種類
                - submit:フォームでsubmitが実施されたら
                - foucs:フォーカスした時（フォームに入力するために入力箇所をクリック）
                - blur:フォーカスアウトした時（フォームで入力箇所にクリックしてフォーカスしていたが、別の場所にフォーカスが移った時）
                - change:フォームで値が入力されて、値が確定したら
                - input:フォームで値が入力されたら（入力中で発生する）
        - CSSの様にスタイルを変更する方法

### AI
- 必須のエラーバリエーション
    - name:最大３０文字
    - email:emailアドレスの形式になっていること（※type=textにて試す）
        - 正規表現とは？
        - emailだということを断定するには？
    - content:最小２０文字で最大２００文字とかに設定
- その他
    - 現在「error」と表示されているところに表示させる
    - errorの文字を変更するのも忘れない

### 備考
- 利用したブランチ
`feature/20200701_edit`

- 本日のPR
https://github.com/empty-canvas/maehara-portfolio/pull/8


## Chapter 6: 2020-07-01

author: @maehara

### お問い合わせ（contact部分）の開発/モブプログラミング（30m）
Driver:maehara
Mob:グッチー

- お問い合わせフォームの全体像の説明
    - Web上に入力フォームを作成し、その情報をGoogleフォームに連携する感じ
- 入力フォームの作成
- formタグ、labelタグ、inputタグの説明
    - formタグのmethod属性の説明（GETとPOST）
    - labelタグのfor属性の説明
    - inputタグのtype,name属性の説明
        - 実際に入力フォームに入力された挙動の確認（URLにどんな値が表示されるか）
        - フロントエンドでもサーバーサイド側の知識が必要になる部分の説明

### AI
- 今回作成した入力フォームにエラーなどを発生させた時に崩れない様に調整しておく（前原）

### 備考
- 利用したブランチ
`feature/20200701`

- 本日のPR
https://github.com/empty-canvas/maehara-portfolio/pull/6

## Chapter 5: 2020-06-25

author: @wataboru

### イントロ (10m)

- 佐藤の自己紹介
- 前原さんの自己紹介
- 本日の進め方の説明
   - 佐藤がドライバー、前原さんが誘導する
   - 目的は以下の通り
     - 説明しようすることで理解できないところが明確になる
     - 初JOINの佐藤のキャッチアップの目線なども参考になるカも？
  
### 現時点までの開発の進め方の説明と、動作確認 (20m)

- 動作確認
  - git clone
  - エディターで開く
  - (`npm install`)
  - `npm run watch`

- 今までの状況の説明
  1. ポートフォリオサイトを作るという最終目的
  2. デザインは貰っており、コーディングをしている
  3. デザイン通りのコーディングは完了しており、レスポンシブ対応を行っている
  4. 最後の時点では、jQueryが動いているかわからず、ハンバーガーメニューの実装に苦戦している状況

### 開発の進め方の説明／モブプログラミング (30m)
Driver: @wataboru
Mob: 前原さん、山口さん

- ディレクトリ構造の説明（Mob:前原さん）
- Webpackを用いたモジュール管理方法の説明（Mob:山口）
- 新しいコンポーネントを追加するデモンストレーション（Mob:前原さん）
  - footerを仮に制作し、前原さん誘導の元、実装をやってみる
  - その後、佐藤が実装中に思っていたことを話したり、山口さんからの意見ももらいつつ、リファクタリング
- jqueryの動作確認手順説明（山口）
- jqueryを用いたスライドダウンの実装のバグフィックス＆リファクタリング（山口）
  - セレクタ誤りが原因

### 備考
- 利用したブランチ
`feature/20200625`

- 本日のPR
https://github.com/empty-canvas/maehara-portfolio/pull/4

## Chapter 4: 2020-05-28

* 前原ドライバーで先週の続き
    * 〜 20:45 開発
        * ドライバーのやり方
        * リポジトリ名の変更方法
        * XD のプロフィール画像のあるエリアを作り始める
* 作業用リポジトリ
    * https://github.com/empty-canvas/maehara-portfolio
    * [branch: feature/20200528](https://github.com/empty-canvas/maehara-portfolio/pull/1)
        * git 周りの

## Chapter 3: 2020-05-21

* コーディング開始
    * XDファイルを観ながらすすめる
    * 今回はすべて山口がドライバーで流れを見せた
* 作業用リポジトリ
    * https://github.com/empty-canvas/maehara-portfolio

## Chapter 2: 2020-05-16 / 

* フロントエンドのプロジェクト開始準備
    * 参考資料: https://github.com/RikutoYamaguchi/frontend-build-description
    * 実施ログ: https://github.com/naohiro-maehara/bootstrap-carousel-to-vanila-code

## Chapter 1: 2020-04: 

* git 操作勉強
    * https://github.com/empty-canvas/empty-canvas/issues/4
