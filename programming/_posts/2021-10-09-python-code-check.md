---
layout: post
title: "Python コードチェック"
date: 2021-10-09 10:03 +0900
dir: /programming/
tags: ['Python', 'メモ']
description: "Python コードチェックまとめ． vscodeでの設定"
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [メモ](#メモ)
- [参考](#参考)

### Key word
- Python, Visual Studio Code
- linter, formatter
- flake8, black

### はじめに
Pythonの環境を構築する際のlinter, formatterの設定をメモしておきます．

### メモ
#### 準備
必要なものをインストール
```
pip install flake8
pip install black
```

#### vscode設定
```json
{
  "python.languageServer": "Pylance",
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": false,
  "python.linting.flake8Enabled": true,
  "python.linting.lintOnSave": true,
  "python.formatting.provider": "black",
  "python.linting.flake8Args": [
      "--max-line-length",
      "90",
      "--ignore",
      "E203, E266, E501, W503, F403, F401"
  ],
  "python.formatting.blackArgs": [
      "--line-length",
      "119",
      "--ignore",
      "W503"
  ],
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
      "source.organizeImports": true
  }
}
```
`W503`（２項演算子の前で改行）などflake8のルールをblackとの兼ね合いで無視するところが少し気になる．

### 参考
- [Blackできれいに自動整形！flake8とBlack導入と実行](https://qiita.com/tsu_0514/items/2d52c7bf79cd62d4af4a)
- [Black: Python のソースコードを自動整形するツール](https://org-technology.com/posts/python-black.html)
- [もうPythonの細かい書き方で議論しない。blackで自動フォーマットしよう](https://blog.hirokiky.org/entry/2019/06/03/202745)
- [flake8](https://pypi.org/project/flake8/)
- [black](https://pypi.org/project/black/)