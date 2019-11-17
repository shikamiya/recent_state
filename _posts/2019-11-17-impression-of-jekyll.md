---
layout: post
title:  "impression of jekyll"
date:   2019-11-17 04:00:00 +0000
---

### Introduction

見れば分かるとは思いますが、このページは Jekyll で生成しています。

GitHub Pages はページの生成に Jekyll を使用しているため、
Jekyll のソースファイルを push するだけでページの公開が可能です。

### Setup

Jekyll や GitHub Pages のドキュメントにセットアップ方法は書いてあるので
基本はそれに従うだけですが、いくつかハマったポイントがありました。

まず、 GitHub Pages の現在サポートしている Jekyll のバージョンは、
[Dependency Versions](https://pages.github.com/versions/) に
書いてありますが 3.8.5 です。
Jekyll の最新リリースの 4.0 はまだ使用できません。
といっても、それらのバージョンは `github-pages` gem によって管理されているため、
意識する必要はありません。

ただ、 `github-pages` gem を使用する場合は `Gemfile` から `jekyll` gem を削除する
必要がある(`github-pages` gem の依存で適切なバージョンが入る)のを見落として
しまい、依存関係のエラーが出てしまっていました。

また、デプロイ先 URL がサブディレクトリの場合(このページもそう)、 Jekyll の `baseurl` に
サブディレクトリを指定する必要があります。未設定だとリンク先が正しくなくなり、CSS ファイルも
読み込めなくなります。

この指定をした場合、ローカルでの動作確認(`jekyll serve`)の URL も
このディレクトリ下になります。
例えば、このレポジトリで `jekyll serve` を実行すると、 `http://localhost:4000/recent_state` で確認できるようになります。

### Impression

Wordpress 等今までに使ったことのあるブログ向け CMS 等と比べると、
かなりシンプルで楽だと感じます。

Markdown を適当な HTML に変換してくれるだけ、というくらいの感覚で
使っていますが、それでも十分だと感じています。

Ruby は最近あまり書いていませんが、 Jekyll を使うだけなら Ruby の
知識はほとんど要求されないですし……。

### Conclusion

Jekyll は素晴しいが、あらゆるところで `.nojekyll` 見かけるのは
ちょっとスマートではないように感じます。
