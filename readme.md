# はじめに


記事の執筆には、Markdown形式を利用してください。
Markdownにはさまざまな流派がありますが、GitHub Flavored Markdown（[https://github.github.com/gfm/](https://github.github.com/gfm/) ）をベースとした書式を採用します。

書籍を執筆するための形式として考えると、Markdownには不足している機能が多々あります。
しかし、次のような利点があるので、Markdownを採用することにします。

* 最低限の構造しかないので、見た目でごまかせる余地が少ない
* 原稿を著者自身が再利用してもらいやすくしたい
* ラムダノートで販売する際のスタイルは、原稿の形式がなんであれ、別に考えなければならない

以下では、節や項といった記事の大構造、および、段落やコードや図表といった記事の小構造について、
執筆にあたって気を付けていただきたいことや記述方法のお願いをまとめます。

* 目次
  * [記事の大構造](https://github.com/ta96o/Dev_Env/blob/main/readme.md#記事の大構造) ：見出しの構文、考え方
  * [記事の小構造](https://github.com/ta96o/Dev_Env/blob/main/readme.md#記事の小構造) ：段落や図表、コードなどの構文、考え方
  * [本文の書き方](https://github.com/ta96o/Dev_Env/blob/main/readme.md#本文の書き方) ：本文の考え方
  * [書式に関してサポートしないこと](https://github.com/ta96o/Dev_Env/blob/main/readme.md#書式に関してサポートしないこと) ：スタイルに関する制限と注意事項

## 記事の大構造

記事全体をどう構成するかは、解説する内容や目的（情報の要約かチュートリアルか、など）によって異なります。
論文ではないので定型はありませんが、困ったら下記の構成に沿って考えてみてください。

1. 何のために記事を書くか（問題意識を読者と共有）
2. 解説の前提となる情報の整理（読者を記事の土俵に上げる）
3. 主たる解説
4. まとめ、練習問題、関連情報、参考資料など

最上位の階層に対する見出しには、都合により、Markdownのレベル2（ `##` ）を利用してください。

通常、大構造の内部は、さらに構造化したほうが読みやすくなります。
しかし、構造が深くなると読者が迷子になりやすいので、大構造の下位は原則として1段階のみとします。

上記をふまえると、記事全体の構造は下記のようになります。

```markdown
## セクション1の見出し

段落要素

### サブセクション1の見出し

段落要素

### サブセクション2の見出し

段落要素

## セクション2の見出し

段落要素

…
```

## 記事の小構造

記事の本文のほとんどは、段落です。
段落は、文章の意味の最小単位といえます。

以下では、段落および段落を補完する箇条書きや図表、コードブロックなどの要素についてまとめます。

### 段落の書き方

段落を書くときは、以下の2点を気にかけてください。

* ある段落を1つ取り出したとき、その内容を簡潔に要約できるか
* 段落と段落の関係は、全体として伝えたい内容にとって適切か

上記の2点を達成するために、編集でかなり大胆な本文の修正を提案する場合があります。
そのため、差分が見やすくなるように、段落内ではなるべく句点ごとに改行を挿入してください。

段落は次の要領で記述します。

```markdown

空行から次の空行までの文章が、1つの段落になります。
途中で改行しても、新しい段落にはなりません。
むしろこまめに改行したほうが、差分がとりやすくなります。

段落内および段落間をうまく構成すると、言いたかったことが伝わりやすい記事になります。
各段落の内容を自分で要約しながら自分で読み返してみるのがおすすめです。

```

本文で利用可能な記法については、本稿の後半の「本文の書き方」の項を参照してください。

### 箇条書き

段落の主張を見やすく整理することを目的として、必要に応じて箇条書きを利用してください。
言い換えると、箇条書きはあくまでも段落に従属するものとし、箇条書きのみで説明が終わることがないように注意してください。

箇条書きには、連番がつかないものと、つくものがあります。それぞれ以下の要領で使います。

* 箇条書き（Unordered List）

  基本的には連番なしの箇条書きを使います。
  ```markdown
  * 項目1
    * サブ項目は1階層のみ可
  * 項目2
    1. 連番つき箇条書きのサブ項目の例
  ```

* 連番つき箇条書き（Ordered List）

  項目間の順序に意味がある場合や、あとで番号で参照したい場合は、連番つき箇条書きを使います。
  ```markdown
  1. 項目1
  2. 項目2
  ```

### 図

段落の説明を補足することを目的として、必要に応じて図表を利用してください。

画像は以下の要領で配置します。なるべく見出しを付けてください。

```markdown
![キャプション](/path/to/image.data){#fig:id}
```

キャプションとIDを指定した図は、本文から下記のようにして図番号により参照できます。

```
……。図[-@fig:id]に〇〇のようすを示す。
```

### 表

表の書式についてはPHP Markdown Extraの書式（Pandocでいう `pipe_tables` 拡張）が使えます。

* [PHP Markdown Extra のTableに関する説明](https://michelf.ca/projects/php-markdown/extra/#table)

表の記述例を下記に示します。
表のタイトルは、 `Table: ` で始まる行をテーブルの下に記述してください。
本文からの参照方法については後述します。

```markdown

| 右寄せ | 中央寄せ | 左寄せ |
| -----: | :------: | :----  |
| 123456 | 〇       | ABC   |
| 00     | ✔       | あいう |

Table: タイトル{#tbl:id}
```

キャプションとIDを指定した表は、本文から下記のようにして表番号により参照できます。

```
……。表 @tbl:id に〇〇の一覧を示す。
```


### コードブロック

技術書において、プログラムの一部を示したコードブロックは主要な解説対象です。
したがって、コードブロックの提示をもって説明を終わらせるのではなく、そのコードについて日本語で説明を施すようしてください。
具体的には、次のような内容を説明してください。

1. なぜ本文のこの位置でそのコードを提示するのか
2. 何を実現するコードなのか
3. コードの各部にはどのような役割があり、どのように動作するか

プログラミング言語のコメント機能を使ってコード中に動作の説明を付記するのは、上記のうち3のみにしてください。
コメント機能によるコードの動作の補足説明は、コードの中身をしっかり読む段階にある読者にとってはとても有用ですが、初見ではあまり読まれません。
特に上記の1と2の内容については、本文でしっかりと解説するようにしてください。

コードブロックを示すときは、原則として下記の書式を使ってください。
本文からの参照方法については後述します。

````markdown
```{#lst:id python caption="あいさつ"}
def greeting():
   print ("Hello World!")
```

以下は実行結果。

```{#lst:id sh caption="実行結果"}
$ python greeting ⏎
Hello World!
```
````

キャプションとIDを指定したコードブロックは、本文から下記のようにしてリスト番号により参照できます。

```
……。[-@lst:code1]に〇〇の例を示す。
```

コードブロック開始行の `{...}` 内には、本文でコードを参照するときのIDとキャプションのほか、さまざまな属性を記述できます。

#### 構文ハイライト

主要なプログラミング言語については構文ハイライト（モノクロ）に対応しています。

`sh` もしくは `console` は入力画面であるとみなし、次のような特別な表示上の扱いを受けます。

* 出力の背景色と文字色を反転させます（通常は白地に黒文字であるものが黒地に白文字になる）
* 末尾が ` ⏎` の行はユーザ入力を表すものとして太字化する

#### 行番号

コードブロックの左側には原則として行番号を出力します。

行番号が不要な場合には、コードブロック開始行の `{...}` 内に `number="no"` を指定してください。

#### ページ分割

コードブロックは原則としてページ分割されません。

長いコードブロックでページ分割を許可するものは、コードブロック開始行の `{...}` 内に `break="allow"` を指定してください。

### 引用

他の文書からの引用には、下記の書式を使ってください。

```
本文

> 引用文
> 引用文

本文
```

引用のみで説明を済ませることは**絶対に**しないでください。
引用は、本文を補足する目的に限ります。出典も必ず明記してください。

### 補足事項（NOTE）

引用のスタイルの1行めを「`node`」にすることで、本文から脱線する話題や注意書きを記述できます。
「脚注に埋もれさせるべきではないが、本文にするのも違う」ような補足に使います。

````markdown
ここは通常の段落。

> note
>
> Noteの本文は、行頭に「>」を付けた段落として執筆してください。
> 箇条書きやコード片なども挿入できます。
>
> * サブ項目a
> * サブ項目b
>  
> ```
> Hello World!
> ```
>
> Noteの終わりには、空行＋インデントしていない行が必要です。

ここからは次の段落本文になります。
````

### コラム（ASIDE）

引用のスタイルの1行めを「`aside{...}`」にすることで、本文から脱線する話題を見出し付きで記述できます。いわゆるコラムです。見出しは `{...}` に記述してください。

````markdown
ここは通常の段落。

> aside{コラム見出し}
>
> コラムの本文は、行頭に「>」を付けた段落として執筆してください。
> コラム内にも箇条書きや図表、コードなどを挿入できます。
>
> * サブ項目a
> * サブ項目b
>  
> ```
> Hello World!
> ```
>
> コラムの終わりには、空行＋インデントしていない行が必要です。

ここからは次の段落本文になります。
````

### 脚注

脚注が使えます。

* 脚注を挿入する場所に、 `[^anchor]` （角括弧の中に`^`を先頭文字とした一意な文字列）の記法でアンカーを記述
* 脚注の中身は、本文より後ろに、空行を挟んで行頭から `[^anchor]: …` のように記述（アンカーの直後に `: ` で挟んで改行なしで文を入れる）

```
ここは本文です[^anchor]。
文末に脚注を挿入する場合は、この例のように、句読点の前にアンカーを設置してください。

[^anchor]: 脚注の本文。本文に設置したアンカーと同じ文字列段落をには改行を入れないでください。
```

アンカーに使う文字列（上記の例では `anchor`）は、単純な連番でなく、脚注の内容を表す一意なものとしてください。

### ディスプレイ数式

`$$` のみの行から、次の `$$` のみの行までの間に、下記の要領でLaTeXの書式を記述してください。
どのようなLaTeXコマンドに対応するかは未定なので、そのつど相談してください。

```
$$
\hoge
$$
```

この形式で数式以外のもの（図表など）を入れ込むことはしないでください。


### 参考文献

`refs.bib` と命名したファイルに、BibTeXの形式で書誌情報ファイルを用意してください。
   
```
@article{foobar2019,
     author = {Doe, John.},
     title = {FooBar},
     year = {2019},
     url = {http://example.com/foobar},
     ...
} 
```
   
本文では以下のようにしてcitationを記述します（読点の位置に注意）。

```
…… [@foobar2019]。
```

## 本文の書き方

段落などを構成する本文は、敬体でも常体でもかまいません。

以下では、本文における装飾や約物の使い方などを簡単にまとめます。
これ以上に細かいシンタックスやレギュレーションを設定する予定はありません。

### 本文に対する装飾

本文中では、文字列に対する装飾として、下記の書式**のみ**を利用してください（`␣` は半角スペース `U+0020` を意味します）。

* `**文字列**` （文字列を強調）
* ```文字列``` （文字列を等幅で表示。`` ` `` を含める場合には、連続するバックチックで囲む ```␣`` `を含む文字列``␣``` という書式を使う）
* `文字列（[URL](URL)）` （文字列に対して外部のURLを参照。「URL」の部分は同一の内容を入れる。 `[文字列](URL)` のようなURLを見せないリンク形式は不可）
* `$TeX書式$` （インライン数式）
* 行頭の `★` マーク （行末までを、本文ではなくコメントとして扱う。行頭以外の `★` マークは非コメント）

### 句読点

とくにこだわりがなければ、 `。` と `、` を推奨します。
`．` と `，` 、もしくは `。` と `，` などでもかまいませんが、編集で `。` と `、` に変更する可能性があります。

いわゆる半角の `.` および `,` は句読点としては使わないでください。
  
疑問符および感嘆符をどうしても使う場合は、それぞれ全角記号を使用してください。
すなわち、 `？`（`U+FF1F`）および `！` （`U+FF01`）を使ってください。
  
コロンやセミコロンを使う場合も、全角とします。
すなわち、 `：` （`U+FF1A`）および `；`（`U+FF1B`）を利用してください。
  
### 和欧文間のスペースについて

日本語の文字と英数字間にスペースは入れないでください。

### 括弧類について

本文中での補足には、なるべく全角の丸括弧 `（` および `）` を使ってください。
それぞれ、具体的には `U+FF08` および `U+FF09` です。

本文中で文字列を意味的に切り出したい場合には、基本的に鍵括弧（`「` および `」`）を使ってください。
言い換えると、日本語を切り出す際にダブルクォーテーションは使わないでください。


## 書式に関してサポートしないこと

書式に関して期待されるであろう事項のうち、下記の点に関しては最初からサポートしないものとします。

### 一定の見た目

WebブラウザやPDFで、上記の書式がどのような見た目で表示されるかは、書式から一意には定めないことにします。
GitHubに貼り付ければ、そのWebサイト上で一定のスタイルでレンダリングされると思いますが、そこでの表示を整えることはがんばらないでください。

そもそも上記の定義には、GitHub上で意図したようにレンダリングされない要素もいくつかあります。
たとえば、そもそも数式に関しては、GitHubで意図通りにレンダリングされることはありません。
コメントについても同様です。
脚注についても、本文以外の場所に表示されるようなものはありません。
