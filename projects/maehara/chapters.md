# Chapters

## Chapter 23 :2020-02-02

author: @maehara

### 内容

- 自分の課題感の共有
    - UI/UXに関するセンス・経験値不足
    - 技術力不足
        - ブラウザ依存に対する課題でブラウザでの動作確認が甘い
            - Windows
                - Edge, IE, Chrome, >>>, firefox, Opera
            - Mac
                - Safari, Chrome, Edge, >>>, firefox
            - iPhone
                - Safari,  Chrome
            - Android
                - Chrome
        - 環境
            - ローカル環境のサーバーで挙動確認する
    - 相手の要求を先読みする力？(応用力、非指摘事項への配慮)
- 課題感に対してこの会をどうしていくか
    - わたるんさんが用意してくれたHPを作成
        - タスクとして、どこまでやっておくということを会の最後に決める
        - できた部分の説明を行い、なぜこのようにしたのか。意識し、それに対してのFBをもらう
            - なんでこのアニメーションにしたのか
            - なんでレスポンシブ でこうしたのか
        - ブラウザ間でどうなっているのかも確認
        - ローカル環境のサーバーを作成
- 今回は一旦HTMLやCSSなどをベタ書きでやっていく
    - 今後は、テンプレートエンジンを利用していきたい
        - pug
        - ejs

### 今回のタスク
- ローカルサーバーをたて、下記のページを確認できるようにしておく
    - トップページはheaderとfooter
    - 採用情報
    - プライバシーポリシー


## Chapter 22 :2020-1-29

author: @maehara

### 内容

- git-flow,github-flowについて
    - github-flow
        - 今自分が今回の案件でやっていたような感じ
            - mainブランチがあって、そこからブランチを切って、対応したらmainにマージしていく(自分の場合は、動かない状態でもプルリク作成して、マージしていたので細かく言うとちょっと違う)
        - main,masterブランチは常にデプロイ（ソースコードを本番環境にリリースさせる）できる状態にしておく
            - ローカルに落とし込んで、ブランチ切るのは変わらないが、動く状態になって、レビューなど確認が終わったら、マージしていく
                - ヘルプやレビューして欲しい場合に、プルリクを作成して、プルリクでやりとり
        - デメリット
            - マージまでの期間が長くなってしまう。
                - チームで開発している場合、別の人がマージしている上からマージすることになってコンフリが発生する
                    - コンフリはいいが、その時に別の人が要素を削除や構造を変えていた場合に、自分が作成したプルリクでバグが発生してしまう可能性も出てくる
    - git-flow
        -  基本的に５つのブランチを軸にしていく
            - developブランチ
                - 開発を行うためのブランチ。開発者は、主にこのブランチ上で作業を行う。次に紹介するfeatureブランチなど、他のブランチで行った作業は、ここにマージされる
            - featureブランチ
                - 主要な機能を実装するためのブランチ。機能の実装やバグフィックスなど、タスクごとにfeatureブランチを作成し、作業を行う
                    - 分岐元： develop ,マージ先： develop
            - releaseブランチ
                - リリースの準備を行うためのブランチ。プロダクトをリリースする前に、このブランチを作成し、微調整を行う。releaseブランチを作成することで、リリース準備と次のバージョンに向けた開発のコードを分けることができる
                    - developブランチで開発を行っていき、リリース段階になった時に作成し、完了したら、developブランチとmasterブランチにマージ
                    - 分岐元： develop,マージ先： develop と master
            - masterブランチ
                - リリースしたソースコードを管理するためのブランチ。リリース作業を行うと、releaseブランチはmasterブランチへマージされて、リリースタグが打たれる。開発者は、このブランチへのコミットは行わない
            - hotfixブランチ
                - リリースされたソフトウェアに緊急の修正を行うためのブランチ。このブランチでの修正内容は、すぐにリリースされるので、hotfixブランチはリリースを管理するmasterブランチへマージされる
                    - 分岐元： develop,マージ先： develop と master
        - コマンドも限定的にできる
            - start	ブランチを作成
            - finish	develop、もしくはdevelopとmasterへマージし、ブランチを削除
            - publish	ブランチを共有リポジトリで公開
            - track	共有リポジトリからブランチを取得
            - pull	共有リポジトリ上のコミットを取得
            - rebase	ブランチ上でリベースを行う
    - github-flow,git-flowについては基礎になるから、理解しておく必要がある


### 勉強になったサイト
- エンジニアライブログ
    - https://tomoyuki65.com/lets-learn-github-flow/
- Gitブランチを使いこなすgit-flow／GitHub Flow入門（1）
    - https://www.atmarkit.co.jp/ait/articles/1311/18/news017_2.html
- git-flowの使い方
    - https://rfs.jp/server/git/03git/howto-git-flow.html
    
## Chapter 22 :2020-1-21

author: @maehara

### 内容

- モブレビュー
    - 自分の書いたコードとわたるんさんが書いたコードを自分が説明
        - FB
            - 単数形なのか複数形なのか意識しよう
                - 配列として定義している変数でも単数形として、定義しているので、読み手からすると、違和感が出てくるし、誤解を生んでしまう
    - 自分が書いたコードとわたるんさんが書いたコードをわたるんさんが説明
        - FB
            - 関数の中に関数を定義しないようにしよう。１つの関数で処理する内容は１つ。
            - 今回のケースで言うと、「reader.on('close', () => {}」と言う関数が大元にあって、その中で、さらに関数を定義してしまっている。なので、readerの外に出して、定義して利用していく  
                - 問題を解いていて、そこが関数でとかを考えていなかった。readerのなかで処理が完了すればOKと言うことしか考えてなかった
- 自分で思ったこと
    - いらない変数を定義していたり、関数化をしている

### 備考
リーダブルコードを読み進める


## Chapter 21 :2020-12-10

author: @maehara

### 内容

- モブレビュー
    - paizaC083
        - 変数や関数の命名については、もっと意識
            - target〇〇とか付けがちだけど、前後の文脈などから把握するようになってしまうので、好ましくない。できればその単語だけでそこには何が入ってくるのか読み取れるように命名していく
        - ループ処理には、いくつかあるが、なぜそのループ処理の方法を選択したのかを特性を理解した上で書いていく
        - javascriptでは分解代入ができるので、paizaくらいであればどんどん使って可読性を上げていってもいいね
        - 出力方法だが、今回みたいに「＋」で結合していって出力するのもいいが、やっぱり読みにくいかもしれないので、「変数展開」という形で出力できるようにもしておこう
        - グッチーさんやかずさんのコードをみて、自分じゃ使えないというコードを調べて自分のものにしていく
- かずさんがpaizac050を解いているのを見る
    - やりたいことがあったとして、こうやることと同じだよねという視点の切り替えが早い
        - スキルがあるという前提だが、その視点の切り替えはスキルができなくてもできることだから、ここの視点の切り替えが重要だなと感じた
    - 慣れないうちは、疑似コードを書いて整理してから、階層が深い部分からコードにしていく
### 振り返り

- ループ処理の特性
    - map()
        - 配列の順番通り要素を取り出し、コールバック関数によって処理された要素を新しい配列として返す。
        - 返された配列の要素数と処理をした配列の要素数が変わらない
    - reduce()
        - １つの要素を返す
        - コールバックで返された値を蓄積することができる
    - while(){}
        - ループ処理から抜け出すために、ループ内部で増減式を記述する必要がある
        - 前置判定
            - 条件式が{}の前にあり、その条件式がtrueであれば処理をする
            - １回目からfalseの場合は、一度も処理が走らない
        - do{}while()
            - 後置判定 
                - 条件式が最後にきていて、その条件式がtrueであれば繰り返す。
                - 条件式が最初からfalseであっても、一度はループ処理が走る。そして最後に条件式がfalseとなり、２回目の処理は走らない
    - for(初期化式; 条件式; 増減式){}
        - ()内に条件を書いてしまうので、ループ内部で増減式の記述は不要
        - カウンター変数を定義して、その場で指定した通りにループさせたい場合に利用するといい。それ以外は「for in/for of」を利用するといい
        - for in/for of
            - for in:連想配列に利用
                - for (var value in data) {}というようにして、連想配列dataの中の要素を順に取り出していく
                - 注意点
                    - 配列の機能を拡張している場合だと、配列の中だけでなく、拡張された機能についてまで表示されてしまう
            - for of:配列に利用
                - for (var value of data) {}というようにして、配列dataの中の要素を順に取り出していく
                - 注意点
                    - ECMAScript 2015という新しい仕様で使用されているので、対応していないブラウザが存在する
- 補足
    - ECMAScript 2015とは
        - エクマスクリプトといい、javascriptの標準規格のこと。
        - ECMAScriptはバージョン1~続いており、現在はバージョン5~6が大体主流
            - ES5やES6という表記は「ECMAScriptのバージョン5、バージョン6」って意味
            - ES5やES6等の表記以外にもES2015やECMAScript2015等の表記もあり、ES6というバージョンの表記を西暦にするようにしたもの。ES2015=ES6という意味
- 勉強になったサイト
    - https://techplay.jp/column/470
- 変数展開
    - ES2015(ES6)からは``(バッククォート)で囲うテンプレート構文(Template literal)で書くことができるようになり、この中のプレースホルダー形式で記述することをいう
        - 今までは「＋」で連結していた
    - 書き方
        - プレースホルダー「${..}」ようにかく
    - 文字列中で変数を展開できる。
    - プレースホルダー内で計算や関数を呼ぶこともできる。
    - 同期系の処理はできない


### 備考
- 利用したブランチ（利用したコード）
https://github.com/empty-canvas/paiza_code/tree/main/C050
https://github.com/empty-canvas/paiza_code/tree/main/C083

- 本日のPR
なし

## Chapter 20 :2020-12-3

author: @maehara

### 内容

- モブレビュー
    - paizaで書いた自分のコードを説明し、レビュー＆わたるんさんに自分のコードレビュー＆グッチーさんとかずさんのコードもレビュー
        - 自分が説明するのと、自分が書いたコードを別の人が説明することで感じたこと
            - 名称がめちゃめちゃわかりにくい
                - 書いている時は、あー汚いけどわかるか。という気持ちになりがちだが、説明と（特に）「他人に説明してもらう」という時に、めちゃくちゃ分かり難し、統一性が全くないとめっちゃ実感
            - 条件分岐が多すぎる
                - 考え方をちょっと変えるだけで、１つずつ条件分岐をなくすことができた
                    - 条件分岐が重複
                - もっと視点を変えて！
            - 一つ一つの処理を分解して書いていかないと
        - FB
            - 名称がめちゃめちゃわかりにくい
                - その変数名から、保持しているデータや処理内容が連想できない（めっちゃ可読性が悪いし、読みづらい）
                - 自分の付け方だと、むしろその変数名から別のデータや情報を想像してしまうことが多い
            - 条件分岐が重複しているし、わかりづらい
                - A or Bという条件分岐の時は、if(){} else(){}という感じで「else」を使おう
                    if()の()の中身などを正確に理解しないといけないのが可読性を落とす
            - 階層が深い
            - 副作用を考える
                - まだ書いているコードの量が少ないから、考えなくてもできてしまうが、めちゃくちゃ大事。
                - 変数を定義して、その後に格納されているデータを置き換えたりする場合は、別の変数名にして保持させたり、を考えよう
            - 説明できない（説明していて伝わっているかなと心配になったり）、他人が見た時に説明できないと、構造や命名規則がわかりづらいということだから、もっとシンプルに。
            - コードの可読性をもっともっと考える！！！
            - 読み手をイメージ
            - classまでいかなくても、関数化を使っていこう
        - 他の人のコードを見て
            - とにかくめちゃくちゃシンプル！！！！
            - どんな形で持っているのかとかまではまだイメージできなかったりするが、変数名からこういうことを持っているんだろうなと想像できる
            - 2人のコードを見ると、毎回簡単で単純だなーという気持させられるが、第三者が見るということをめちゃくちゃ意識していて、すげー深い
    - その他
        - 配列で持っているのが多いと処理が重くなるイメージを持つ
            - 基本的にループ処理を行うことになり、ループ処理というのは配列に保持しているデータ全てに対して行われるから、データ量が多いとその分遅くなるよねという話
        - 配列とオブジェクトの違い
            - 配列：インデックスで値が管理されている
            - オブジェクト（連想配列）：インデックスではなく、キー（任意の値）で値が管理されている
            - という認識から一歩踏み込んで下記の意識もしよう
            - 配列：順番で管理されている
            - オブジェクト（連想配列）：キーで管理されている。検索性。（極端だが、０、１、２、ときて、次が３でなくて、４や５でいいよ。データとして保持されていて、キーがセットされていることが重要）
                - 順番を保証していない
            - 順番通りに処理をしないといけないなど順番を意識する時は、配列でデータを持っておく
### 備考
- 利用したブランチ（利用したコード）
https://github.com/empty-canvas/paiza_code/tree/main/C081

- 本日のPR
なし
       

## Chapter 19 :2020-11-19

author: @maehara

### 内容

- paizaのC065でモブプロ
    - 「ドライバー：まえはら」だが、途中で思考停止気味になってしまい、わたるんさんのアドバイス頼りになってしまう。。。w
        - 久々に脇汗かいたw
    - 符号と整数だけの状態から、範囲を絞り込むという部分で思考が止まってしまった
        - 今回は事前に1〜100の整数を持った配列から特定整数までの整数を取り除くということで実装（この発想に至らなかったので、いろいろな見方が必要と実感）
        - グッチーさんとかずさんのコードは自分が書いていた内容と違うので、見直して落とし込む
            - パッと見た感じデータの持ち方は似ている

- 反省
    - つまづいて思考停止になっていることがもったいない(→勉強時間が足りない)
    - 文章で考えた手順をコードに落とすのも難しいが、こうしたくてこんなコードを書いているが〜というコードの説明も難しい(→勉強時間が足りない。落とし込みが甘い)

- 次回
    - 事前にモブレビューをやるpaizaを共有しておく
    - 今回はできない（というか途中だったもの）のを対象にやってみたが、できているものをやってみよう

### 備考
- 利用したブランチ
なし

- 本日のPR
https://github.com/empty-canvas/paiza_code/tree/main/C065
（PRではないが、今日やった部分）

## Chapter 18 :2020-11-05

author: @maehara

### 内容

- 案件をもらうときに事前に決めておくこと
    - デプロイ環境
    - ブラウザの対応範囲
    - デザインまでやるかなの対応範囲
    - 指定の実装方法
    - 更新内容
- 今回自分がやる無料のLP作成(まだ全然決まっていない前提でも)
    - ドメインとか後悔する場所などを決めるといい
    - 更新頻度とかも確認
- その他
    - 今は調べて参考にするのは、リファレンス一択でいい
    - JavaScript Primerもみる（Todoアプリのところもやってみるのがいいよ）
    - LP作成でデザインを考える時に、レイアウトとかUIとに盗作は基本ない
        - ロゴはある

### 備考
- 利用したブランチ
なし

- 本日のPR
なし


## Chapter 17 :2020-10-29

author: @maehara

### 内容

- 今後の進め方
    - この勉強会では、paizaをメインに進めていく
        - LPなどは独自で進めていく（不明点あれば都度聞く）
    - paizaでやった問題は全てgithubにあげる
        - https://github.com/empty-canvas/paiza_code
        - 書き方
            - (name).(回数).js    
- 意図
    - 他の人がやった問題と同じのをやってもらい、他の人の書いたコードと自分の書いたコードの比較をする
    - いろんなコードに触れて、いろんな書き方を自分に落とし込む

### 備考
- 利用したブランチ
なし

- 本日のPR
なし

# Chapters

## Chapter 16 :2020-10-22

author: @maehara

### 内容

- paizaのC016（先日質問していた問題）をアドバイス通りに簡略化したコードのFB
    - ループ処理をさせるのには、いくつかある。ループだけしたいのか、ループしたものを何かの変数に格納したいのかなどを考えて、メソッドや文を選択
        - 今回は文字列が格納されている配列のなかに、leetsでしている文字列が含まれているかをチェックして、それを別の新しい配列に格納したい。ということで、forやwhileでも問題ないが、『与えられた関数を配列のすべての要素に対して呼び出し、その結果からなる新しい配列を生成する』というmapメソッドを使うことで簡素化することができる
        - mapによって取得した１つの要素がleets（連想配列）に含まれているかを「〇〇 in □□」や「〇〇.hasOwnProperty(□□)」で含まれている場合、trueというブール値で返すので、三項演算子で値を返してあげる
    - アロー関数について
        - 基本的な構文を理解しよう！！！
            - {}をつけたら、returnをつけないといけないなど（引数が１つの場合はいらない）
    - {}を利用する時
        - 短い場合は、{}はつけないことが多い。
        - つまりは、長くみづらいコードなどのときに、これを利用して改行入れたりと、可読性がよくなるなとなった時につけたりする。なんでもつけりゃいいってものではない。

- paizaのC043をやってみる
    - 時間内にできなかった。。。。
        - 何度もループさせてということではなく、１度のループ処理で判別させるということを考える
        - データを配列でもつか、連想配列でもつかを考える
            - 配列というのはどういうものか。連想配列はどういうものか。２つの違いは？
                - 配列　　→indexという０から始まる整数で管理されている
                - 連想配列→keyとvalueが対となって管理されている
                - 違い　　→連想配列：知りたいものベースで印をつけて管理できるのと配列：知りたいものの集合値（その中で区別するのが大変）という違い

### 備考
- 利用したブランチ
なし

- 本日のPR
なし


# Chapters

## Chapter 15 :2020-10-22

author: @maehara

### 過去２回の分のまとめ

- paizaのFB
    - 無理に関数化しすぎる。もう少し下記のことを意識していこう
        - 変数ってなんで使うの？
        - 関数ってなんで使うの？
    - 難しく（複雑に）考えすぎている
    - 可読性を意識する
        - 明日の自分が見ても読みやすいように考えてコードを書いていく
    - Cにチャレンジしよう
        - 少しずつでも難しいことにチャレンジして成長速度を高めよ

- githubの質問
    - 質問のためgithubにあげたが、あげたいディレクトリではなく、その上位のディレクトリをマージさせてしまって、解消方法がわからない
        - 一旦リポジトリ自体の削除し、再度作成
    - 原因
        - あげたいディレクトリに.gitが作成されていない状態だった。
        - 上位のディレクトリには.gitが作成されていて、それを起点にgit addからcommitしてしまった
    - 対処方法
        - workspaceにある.gitを「rm -rf .git/」で削除
        - airbnbディレクトリで「git init」からpushまで行う

- 模写しているLPの画像を表示できない
    - cssで画像を指定した時にエラーが吐かれてしまうのは、aliasの設定ができていないのが原因
    - HTMLとCSSでは画像ファイルを分けたほうがいい
        - 利用するloaderやプラグインが違うから
            - HTMLー「copy-webpack-plugin」、CSSー「url-loader(file-loader)」
    - この辺りはグッチーさんのプルリクを見直して落とし込む

- FB
    - 模写をするなら、模写だけをする
        - webpackにも慣れておこうということで、利用していたが、つまづく部分が増えて間違えている部分の特定に時間がかかってしまう
        - 返って時間かかってしまう
            - めっちゃ自覚してた。。w

### 備考
- 利用したブランチ
feature/fix-img-load

- 本日のPR
https://github.com/naohiro-maehara/isara-practice/pull/1

## Chapter 14: 2020-09-24

author: @maehara

### 過去３回分のまとめ

- タイムカードというシステムを作ろう！となった時に、どんな機能が必要か考えてみよう！！
    - 意図
        - 最小単位で機能を分解していくイメージを養う
        - コードを書く時に、エンジニアがイメージしていることを体験してみよう
        - この情報はどこに持っておくべきなの？やそもそもその情報はいるの？とかの整理する力を養う（今回はあくまでもこんなふうに考えていくといいというイメージを養う）

- PaizaとCodewarsというプログラミング学習の開始
    - 一旦Paizaからやっている（楽しいね）
    - 教材でインプットがメインとなっていたから、アウトプットしていくのは楽しいし、アウトプットして初めてわかることが多いね

- ディスプレイの相談
    - ノートパソコンだけだと、画面が見にくくて不便に感じ始めたので、ディスプレイを買いたいが、何がいいのか
        - MacBook Air (Retina, 13-inch, 2019)
            - WQHDの27インチかフルHDの24インチ前後がいいだろう
                - 金額が倍ぐらい違うので、懐事情を見てカウ！！

- 飲み会やろうか
    - 10月10日に決定。新橋の金の羊

- scssで画像を読み込もうとするとエラーになり、読み込めない
    - url-loaderだけでなく、file-loaderも必要
        - この辺を調べて、エラーを解消してみよう

### 備考
なし


## Chapter 13: 2020-08-27

author: @maehara

### validateのリファクタリング
driver: かずさん

### 講義内容
- Validatorクラス内のリファクタリング
    - 目的とPoint
        - 目的「シンプルにできるとこはシンプルにして、コードの可読性を高める。不要な変数などの削除」を意識して、コードをみていく
        - 細かく区切りをつけ、動作確認して問題ないことを確認後コミットしていく
    - 実際に行った内容
        - constructor内の変数validatorの定義は現時点でどこにも利用されていなかった　→　削除
            - 未定義の変数があった場合に変数名の色が変わるアプリをVScodeでないか確認する
        - onValidatedメソッドの削除とaddErrorメソッドの名称変更、onValidatedCallback関数の名称変更
            - onValidatedメソッド
                - Htmlのエラー値を変更させ、表示させる関数をonValidatedCallbackに代入させているメソッドだった
                    - 今回はメソッド自体がなくなったが、残すとしたらsetValidatedという方がパッとわかるかも
                - onValidatedCallback関数を少し変えたため、不要になり削除
            - addErrorメソッド
                - エラーを追加し、onValidatedcallback関数を実行するメソッドの想定だったが、現状、そうなっていなかったのかもしれない。（ただ見返してみると、ちょっと引っかかってしまうので、かずさんにもう一度聞いてみる）
            - onValidatedCallback関数
                - addErrorメソッドにて実行され、{name:〇〇}の様なオブジェクトを引数にもち、onValidatedメソッドのコールバック関数を実行させていた
                    - そのため、onValidatedメソッドを無くして、onErrorメソッド{name:〇〇}の様なオブジェクトを引数に受け取り、Htmlのエラー値を変更させ、表示させる関数させた

### AI
- VSCodeで未使用の変数を可視化する
- 『javascript 連想配列 key 変数』調べて見てください

### 備考
- 利用したブランチ
feature/refactor_20200827

- 本日のPR
https://github.com/empty-canvas/maehara-portfolio/pull/16

## Chapter 12: 2020-08-20

author: @maehara

### validateのリファクタリング
navigator: わたるんさん

### 今回の講義までに自分でやった部分の説明
- addErrorメソッドの作成、onValidated関数を作成し、エラー文言を表示させる
    - 変なミスはあったが、表示はできる様になった

### 反省点
- グッチーさんに言われた内容での実装ができなかった
    - 特にonValidated関数部分での変数errorがオブジェクトではなく文字列を格納させていること
        - そのため、if文で条件分岐をして、同じ様なif文がname,email,contentそれぞれで発生していた
- validateメソッドの中のif文のエラーメッセージのリファクタリングの忘れ
- このメソッドにはこの役割（addErrorならエラーメッセージを受け取ってerrors[formName]に格納してonValidatedCallbackを呼び出すまで行う）を意識できていなかった

### 講義内容
- validateメソッドの中のif文のエラーメッセージのリファクタリング
    - if文でエラーメッセージをerrors[formName]に格納していたので、これをaddErrorメソッド内で行わさせる
        - メリット
            - 機能を追加した時に、みに行く部分がへる。（つまり修正する箇所がへる）
            - コードをそれだけ入力するので入力ミスがへる
        - 関数への引数に変数があっても問題なく動作するの知った
            - カラクリ
                - 引数が評価されるタイミングより前に、変数が評価され展開されていれば問題なく利用できる
                    - addError(formName, `${rule.label}は必須です`)
                        - ${rule.label}が評価され、'名前''メールアドレス'などの文字列が展開され、addErrorの第２引数に「名前は必須です」という文字列が渡される
- javascriptの基礎を自分でやろう！！
    - オススメ本：改訂新版JavaScript本格入門 ~モダンスタイルによる基礎から現場での応用まで 
        - とりあえず買ったww

### AI
- onValidate関数のリファクタリング
    - 引数はオブジェクトで受け取ることで、if文を利用しなくてすむ

### 備考
- 利用したブランチ
なし

- 本日のPR
なし

## Chapter 11: 2020-08-13

author: @maehara

### validate作成
navigator: グッチーさん

#### 今回の講義までに自分でやった部分の説明
- とりあえず、わたるんさんやグッチーさんに教えてもらったコードを自分のjsで置き換えて書いてみた
    - 結果は当然動かない
    
#### 自分でやった上で講義を受けた収穫
- 文字数のエラーを２つ用意して、項目によって使えわけないといけない部分でグッチーさんの見本を元に自分のjsにカリー化した関数を書けた
- インスタンスが作成されるきっかけがどうしても生み出せずhtmlに「onblur=""」として呼び出した（結論はaddEventListenerを利用する。なぜかこれを使わないんだと思い込んでいた）
    - jsの処理をhtml上に直接書き込みはしないということの発見
        - vueはこれを推奨している

### 講義内容
- classとは
    - 設計図（わかりにくい）
        - 動作や状態を定義した構造のもの。（これもわかりにくいかも）
            - ここで指定した動作などは、ここでインスタンスを作成した場合、必ずここで定義した動作をした上で処理がはじまる（わかりにくいかなーww）

- カリー化とは
    - 複数の引数を取る関数を１つの引数をとる関数に変えること（うまく記載できないが、こんなイメージ）

const rule = {shouldCheckRequired: true,shouldCheckEmai:true}が定義されていたとする
- if(rule.shouldCheckRequired && !this.checkRequired(value)){処理内容}の説明
    - rule.shouldCheckRequiredが「true」かつ!this.checkRequired(value)がfalseの時に実行されると読み取っていたが違う
        - 間違ってはいないが、(1 && 2)となっていた場合、１がfalseの時点で２の判定は行われず、if文内の処理内容が作動しない
            - つまり(2 && 1)としていた場合、２の判定が入って通過したら１の判定が入る。という様に２の判定が行われてしまう
    - ruleが「shouldCheckEmai」を持っていた場合は、このif文の条件「rule.shouldCheckRequired」に合致しないので、if文の処理内容は動作されない

- 変数を定義する部分を意識する。
- 利用している変数が定義されているか意識する

- コールバック関数とは
    - 別の関数（高階関数）によって実行される関数
        - ここはもっと知見を深めていく必要あり

### AI
- コールバック関数を利用して、エラーを表示させる関数を完成させる
- validate()内のリファクタリング


### 備考
- 利用したブランチ
なし

- 本日のPR
なし




## Chapter 10: 2020-08-06

author: @maehara

### validate作成
navigator: wataru-san

- 7/23に作成していた入力フォームのチェック部分のvalidate作成
    - blur/inputイベントが発生したら、checkRequired()やcheckLength()でチェックする実装をしていたが、問題点があった（機能的には特に支障はない）
        - 問題点
            - コード量が多くなる
            - 今３つの項目のチェックだが、項目を増やす場合にかなり手間

- 最終イメージ：validate関数に引数を渡すと、nameならnameのチェックが走ったり、emailならemailのチェックが走る様にする

- 実装の仕方
    - 今回の講義では、終始混乱して訳がわからなくなった。実装の仕方も何もできなかった

- 振り返り
    - wataru-sanの例を使った値の取り出し方やこれをやりたい（コードベースではなく、挙動ベースで）という部分は理解できていたと思うが、ではそれが関数となって、boolean型で欲しいから、どうする？となると。一気に訳がわからなくなってしまった
    - slackでもらった最終的に書きたいコードはこんな感じというの見て、講義中にイメージしていた最終形態が全く違ったので、最終ゴールを理解できていなかったと感じた（説明してもらって理解していたつもりになっていた）
    - このkeyのときに、複数の関数を走る様にオブジェクトをもつ？という部分から多分よくわかっていなかったんだなと感じた（基礎知識が定着していないんだと考える、、、）

- AI
    - 来週までにSlackで教えてもらった内容を見返し、validateの実装までやってみる

### 備考
- 利用したブランチ
なし

- 本日のPR
なし

# Chapters

## Chapter 9: 2020-07-30

author: @maehara

### 関数名の付け方

- 現状の問題点
    - 第三者が関数をみた時に、その関数がどの様な目的の関数なのかわからない
        - length()関数を作っていたが、lengthは長さを表す時によく用いられる（name.lengthとするとnameの文字数など）用語で、整数を戻り値として取得される様に受け取れるなど。考えていこう

- 関数名の命名規則について
    - その関数が何をする関数なのか、関数名を見ただけでわかる様にする
        - 変数なども一緒

- 相談
    - 関数でこの関数は返り値として「boolean型」が返ってくるねとか、整数が返ってくるねとか文字列が返ってくるねというのが、イマイチピンとこない。。（「boolean型」が返ってくる時がピンとこない）
        - 変数には全て「型」というのを持っている。この型という部分を意識するのがいいかもしれない
        - 今までは実際に何かをやって、そのために必要なものなどを調べて覚えてきたけど、「変数とは？」とか「関数とは？」とか基本の部分の理解を深めていくのが今は必要かもしれない
    - 具体的には、function checkLength(value, min, max) { return min <= value.length && value.length <= max; }をすぐに返り値として、「boolean型」が返ってくるというのがわからない（前回グッチーさんとかに説明してもらいながらやったので、「boolean型」が返ってくるのはわかるが、これを別のところで見たら、わからない）
        - 比較演算子を利用していて、比較演算子は「A が B と等しければ（大きければなど） true(真)、さもなくば false(偽) を返す」決まっているので、これを知っていればパッとわかったりする

### 今後
土台を固めていく。基礎の部分の理解を深めていく

### 備考
- 利用したブランチ
なし

- 本日のPR
なし


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
        - 下記の①の場合はtrueを、②の場合はfalseを返す関数
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
