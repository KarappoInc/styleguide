# Gitコミットメッセージのガイドライン

## はじめに

本文書は、株式会社KarappoでのGitのコミットメッセージに関する規準を定めるものである。


## 目次

- [頻出ワード](#frequent-words)

<a name="multiple-lines"></a>
## 複数行に渡るメッセージ


<a name="frequent-words"></a>
## 頻出ワード


### Cleanup(: xxx)

例：

- `Cleanup`
- `Cleanup: remove trailing white spaces`

リファクタリング未満の極単純なコード整理。そのコミットが動作に影響を及ぼさない場合にのみ使用することで、ログを遡る時に無視することができる。

### fix typo

例：

- `Fix typo`
- `Fix: Style breaking in about page`

綴り間違いや漢字変換ミスなどの修正をした際に使用。


### wip: xxx

例：

- `WIP: use babel`

`Work In Progress`の略。まだ修正の途中でコミットしたい時に使う。この時点では正常動作しないことが明示される利点がある。**[SHOULD] ただし、実装完了した段階で`rebase -i`でcommitをまとめ、メッセージを修正するべきである。**
