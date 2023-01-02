---
layout: post
title: "Python コードチェック"
date: 2021-10-09 10:03 +0900
dir: /programming/
tags: ['Python', 'メモ']
description: "Python コードチェックまとめ． vscodeでの設定"
---
## Key word
- Python, Visual Studio Code
- linter, formatter
- flake8, black

## はじめに
Pythonの環境を構築する際のlinter, formatterの設定をメモしておきます．

## メモ
### 準備
必要なものをインストール
```
pip install flake8
pip install black
```

### vscode設定
```json
{
  "python.languageServer": "Pylance",
  "python.analysis.diagnosticSeverityOverrides": {
      "reportGeneralTypeIssues": "none" // np.piなどでerrorが出るので対処
  },
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": false,
  "python.linting.flake8Enabled": true,
  "python.linting.lintOnSave": true,
  "python.formatting.provider": "black",
  "python.linting.flake8Args": [
      "--max-line-length",
      "88",
      "--ignore",
      "E203, E266, E501, F403, F401"
  ],
  "python.formatting.blackArgs": [
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

## 参考
- [Blackできれいに自動整形！flake8とBlack導入と実行, 2021-10-09](https://qiita.com/tsu_0514/items/2d52c7bf79cd62d4af4a)
- [Black: Python のソースコードを自動整形するツール, 2021-10-09](https://org-technology.com/posts/python-black.html)
- [もうPythonの細かい書き方で議論しない。blackで自動フォーマットしよう, 2021-10-09](https://blog.hirokiky.org/entry/2019/06/03/202745)
- [flake8, 2021-10-09](https://pypi.org/project/flake8/)
- [black, 2021-10-09](https://pypi.org/project/black/)
