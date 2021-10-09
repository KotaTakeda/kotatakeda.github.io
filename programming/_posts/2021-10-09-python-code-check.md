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
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": false,
  "python.linting.flake8Enabled": true,
  "python.linting.lintOnSave": true,
  "python.formatting.provider": "black",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
      "source.organizeImports": true
  }
}
```

### 参考
- [Blackできれいに自動整形！flake8とBlack導入と実行](https://qiita.com/tsu_0514/items/2d52c7bf79cd62d4af4a)