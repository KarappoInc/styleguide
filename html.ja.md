# 目次

- [Ruby バージョン](#ruby-version)
- [インデント](#indentation)
- [空白](#whitespaces)
- [空行](#empty-lines)
- [文字エンコーディングとマジックコメント](#character-encoding-and-magic-comments)
- [1行の文字数](#line-columns)
- [数値](#numbers)
- [文字列](#strings)
- [正規表現](#regular-expressions)
- [配列](#arrays)
- [ハッシュ](#hashes)
- [演算式](#operations)
- [代入式](#assignments)
- [制御構造](#control-structures)
- [メソッド呼び出し](#method-calls)
- [BEGIN と END](#begin-and-end)
- [モジュールとクラスの定義](#module-and-class-definitions)
- [メソッドの定義](#method-definitions)
- [変数](#variables)

# HTML/CSS コーディング・ガイドライン

## はじめに

本文書は、株式会社Karappoでの HTML/CSS コードのスタイル規準を定めるものである。
受注案件でクライアント側に別のガイドラインがある場合は、そちらを優先的に準拠する。
SASSの使用を前提として、


<a name="character-encoding"></a>

## 文字エンコーディング

- **[MUST]** 特別な理由がない場合はスクリプトのエンコーディングは UTF-8 にすること。


<a name="body-class"></a>

## body要素のclassやid

- **[MUST]** idではなく、classのみを付加する

```html
// GOOD
<body class="top ja">
</body>

// BAD
<body id="top" class="ja">
</body>
```

- **[MUST]** ただし、IE6対応が必要なときは、`h1.logo.title`みたいな指定が無効化されるので、その場合はidを振るなどの対応をする。CSS側で`.aaa.bbb`という書き方はNG。


<a name="class"></a>

## classやidの命名規則

- **[MUST]** ハイフンはダブルクリックで一括選択できないエディタが多いため、単語の区切りにはアンダーバーを使用する。

```html
// GOOD
<div class="profile_area">
</div>

// BAD
<div class="profile-area">
</div>
```

**SASS,SCSSを利用する場合**

スタイル定義のためのクラス属性は極力避け、意味的な記述を心がけることで、HTMLをシンプルに保つ。

- **[SHOULD]** 基本的にスタイル定義のための属性は極力避けるが、それ以外に意味付けが難しい場合はこの限りではない。（例：`.left`,`.right`など）
- **[SHOULD]** `h1`,`p`など意味の強い要素は、classはあまり付けないようにする
- **[SHOULD]** `div`,`span`など汎用的な要素は、classなどを付けた方が分り易いことが多いので、適宜命名する。
- **[MUST]** compassなどsourcemapが使える場合は、有効化しデバッグ効率を上げる。

```ruby:config.rb
sass_options = { sourcemap: true }
```

<a name="clearfix"></a>

## clearfix

- **[MUST]** sassのextendを使う

**GOOD**
```html
<div class="nav">
</div>
```
```sass
.nav
  @extend .clf
```

**BAD**
```html
<div class="nav clf">
</div>
```


<a name="directories"></a>

## ディレクトリ構成

- **[MUST]** 以下の構成に従う
```
.
├─ img
├─ lib
├─ script
└─ style
```

<a name="image"></a>

## 画像関係

### ファイル名

- **[MUST]** 見出しなどは、ある程度内容が分かる名前にする。扱う量が多いときはその限りではないが、なるべく分かりやすく。

連番は、並びが綺麗なのは良いが、ファイルを探すときに分かりにくい。
後で、画像や見出しの順番が変わるときに、連番が崩れたりすると気持ち悪い。
（例：スライドショーの順番変更）

- **[MUST]** 以下のように表記を揃える

|                        | ◎ 推奨         | ◯ 可        |
|:---------------------- |:---------- |:---------- |
| **省略語**              |            |            |
| ボタン（リンク、その他UI）  | btn        | button     |
| 図                     | fig        | figure, img |
| ナビゲーション            | nav        | menu       |
| **テキスト関係**          |            |           |
| h1,h2などの見出しで使う画像 | title      |            |
| サブタイトル、リード文      | lead       |            |
| 本文                    | text       |            |
| **その他**              |            |            |
| スライドショーの画像       | slide-XXX  |            |
| 矢印アイコン系            | arrow      |            |
| サムネール画像            | thumb-XXX  |            |

ハイフンで統一`fig-1-2.png`など
→ URLの見た目的に綺麗。

<a name="indentation"></a>

## インデント

- **[MUST]** 1レベルのインデントに2つの空白（スペース）を使用する。水平タブを使用してはならない。






<a name="file-name"></a>

## コンパイル前のファイル名

- **[SHOULD]**  

```
// GOOD
example.html.haml
example.css.sass
example.css.scss
example.js.coffee

// BAD
example.haml
example.sass
example.scss
example.coffee

```