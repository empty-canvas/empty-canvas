# Chapters

## Chapter 7: 2020-07-01

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
