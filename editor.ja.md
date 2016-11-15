# エディターガイドライン

## はじめに

本文書は、株式会社Karappo内でコードを共有するにあたり、必要なエディタの設定についてまとめたものである。

# Sublime Text

Preference > Settings より、`Preference.sublime-settings`に下記を追加。

**[MUST]**

```
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
  "trim_trailing_white_space_on_save": true
}
```

- インデントはタブではなく2スペース
- 行末のスペースは保存時に削除

**[SHOULD]**

```Preference.sublime-settings
{
  "rulers":
  [
    80,
    120
  ]
}
```