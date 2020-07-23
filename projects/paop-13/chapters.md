# Chapters

## Chapter 1: 2020-07-22

author: @paop-13

### サンプルサイトコーディングの続き

Driver:paop-13  
Mob:RikutoYamaguchi

### htmlタグについて

- figure  
divでやっても良いけど、figureのほうがSEO効果があったりする。
- figcaption  
figure内にキャプション（文字）をつけれる

https://developer.mozilla.org/ja/docs/Web/HTML/Element/figure

`ex)`

```
<figure id="kaeru">
  <img src="../images/kaeru.gif" alt="葉っぱを傘代わりにするカエル">
  <figcaption>カエルの生態</figcaption>
</figure>
```

**SEOについて**

https://www.itra.co.jp/webmedia/what-is-figure-element.html

### reset.css / normarize.css

- reset.css  
すべてが無になる。h1、pとかも同じスタイルになる。
- normarize.css  
すべてのブラウザで同じスタイルに整える。h1、pのスタイルは違う。

https://magazine.krowl.jp/3441/  
https://meyerweb.com/eric/tools/css/reset/  
https://necolas.github.io/normalize.css/  

### cssの優先順

後読み優先。なのでreset.cssは最初に読み込む。

※ これはscssとかでも同じ。

### cssプロパティー

- background-size  
  https://developer.mozilla.org/ja/docs/Web/CSS/background-size
  - cover: 要素を満たすようにサイズを広げるという意味
- position
  - relative  
  表示領域親要素にできるからという意味
  - absolute  
  親要素からの絶対位置要素
  - fixed  
  view portに対する（見えている領域）の大きさから見た位置
- top/right/bottom/left  
  デフォルトはautoになる。
- line-height  
  数字を指定するとfont-sizeの倍率になる。2だとfont-sizeが16pxだったら32px。ブログの本文とか長文なものは1.6ぐらいが見やすい。
- font-weight  
  `bold` みたいな文字指定と `500` みたいな数字の指定がある。 bold = 700。  
  https://developer.mozilla.org/ja/docs/Web/CSS/font-weight
- margin/padding  
  そのheadingからmarginがなくなってもheadingはhedingの見た目でいるか。なくなっても要素単体がちゃんとしたスタイルになるかどうか。

### レイアウトの当て方のコツ

atoms  
余白感とか、文字の要素とかレイアウトの要素をわけてあげる

### xdでpxをみるところ

マウス当たっているところaltを押すとでてくる

### 備考

- 本日のPR
https://github.com/paop-13/front-learn/pull/1
