# 概要
主に数学・プログラミングについてまとめています．

[数学PDFライブラリ](https://kotatakeda.github.io/math/pdf_library)

# 構成
- [ホーム](https://kotatakeda.github.io/)
- [数学](https://kotatakeda.github.io/math/)
- [プログラミング](https://kotatakeda.github.io/programming/)
- [about](https://kotatakeda.github.io/about/)

# ローカルでの実行（macOS）
macOS 付属の Ruby ではなく，Homebrew の Ruby 3.3 を使用します．
以下の `PATH` 設定は現在のターミナルに適用されます．

```sh
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:/opt/homebrew/lib/ruby/gems/3.3.0/bin:$PATH"
bundle config set --local path vendor/bundle
BUNDLE_VERSION=system bundle install
bundle exec jekyll serve
```

上記は Apple Silicon Mac の Homebrew パスです．Intel Mac では `/opt/homebrew` を `/usr/local` に置き換えてください．
