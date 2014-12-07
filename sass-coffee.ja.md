# Sass/Coffeescript コーディング・ガイドライン

## はじめに

本文書は、株式会社Karappoの Sass,Coffeescript コーディング・スタイル規準を定めるものである。
HTML・CSSの基本部分は[HTML/CSS コーディング・ガイドライン](./html.ja.md)を予め読んでおくこと。

## 目次

- [body要素のclassおよびid属性](#body_class_id)
- [clearfix](#clearfix)
- [ディレクトリ構成](#directory)


<a name="body_class_id"></a>
## body要素のclassおよびid属性

スタイル定義のためのクラス属性は極力避け、意味的な記述を心がけることで、HTMLをシンプルに保つ。

- **[SHOULD]** 基本的にスタイル定義のための属性は極力避けるが、それ以外に意味付けが難しい場合はこの限りではない。（例：`.left`,`.right`など）
- **[SHOULD]** `h1`,`p`など意味の強い要素は、classはあまり付けないようにする
- **[SHOULD]** `div`,`span`など汎用的な要素は、classなどを付けた方が分り易いことが多いので、適宜命名する。
- **[MUST]** compassなどsourcemapが使える場合は、有効化しデバッグ効率を上げる。

config.rb
```ruby
sass_options = { sourcemap: true }
```

<a name="clearfix"></a>
## clearfix

- **[MUST]** sassのextendを使う  
理由：スタイル定義は、極力CSSに集約し、HTML側には記述しない


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

<a name="directory"></a>
## ディレクトリ構成

- **[MUST]** 以下の構成に従う

```
.
├─ _assets
│   ├── database
│   │　　├── create_backup.sh
│   │　　└── backup.sql
│   └── design.psd
├─ img
│   └── logo.png
├─ lib
│   ├── blueimp
│   │　　├── blueimp-gallery.css
│   │　　└── blueimp-gallery.js
│   ├── jquery.min.js
│   └── PIE.htc
├─ script
│   ├── _src
│   │　　└── common.js.coffee
│   └── common.js
├─ style
│   ├── _src
│   │　　├── config.rb
│   │　　└── common.css.sass
│   └── common.css
└─ index.html
```
