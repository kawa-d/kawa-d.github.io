---
title: HugoとGithub Pageでブログ用サイト作ってみました
description: 継続
date: 2023-07-09 00:00:00+0000
draft: false
# image: cover.jpg
# categories:
#     - Example Category
# tags:
#     - Example Tag
---

## 気まぐれ

自分は気まぐれに何か新しいことを始めることは好きですが、なかなか続けれない性格ですが、最近ではそれに反省し、継続することの大切さに気付きました。

このブログも気まぐれで始めましたが、１年間ぐらいは続けたいです。自分の成長や学びをブログに残し、いつか他の人にも役立つ情報を提供できるように努めたいです。充実するといいな～。

自分の仕事は情報システム関連で、その分野に特化した技術ブログをメインに書いていきたいと思っています。ただ、サブテーマとして「継続」を意識しているので、単に日記だけではなく、幅広いジャンルの記事を書いていきたいです。

## Github Page

タイトル通りHugoとGithub Pageでブログ用サイト作ってみました。

Github Pageは静的サイトをホストできるところです。Githubアカウント持ってたら無料で使えます。広告も貼れるらしいです。
[Github Page](https://docs.github.com/ja/pages/getting-started-with-github-pages/about-github-pages)

## HUGO

HUGOは静的サイトジェネレーターというツールで、ブログのような見た目のサイトを簡単に作成してくれるフレームワークです。HUGOにはさまざまなThemeが存在し、優れたデザイナーたちが作ったおしゃれなThemeがたくさんあります。自分の好みに合ったThemeを見つけて、そのリポジトリをクローンし、HUGOに組み込むことで利用できるようになります。Themeを選ぶと、該当するGitHubのリポジトリに移動することができます。Themeのリポジトリには充実したドキュメントが用意されており、Themeの導入が容易になっています。

このブログは「Stack」というThemeを使用しています。使いやすそうでデザインが好きで選びました。

[Stack](https://themes.gohugo.io/themes/hugo-theme-stack/)
[HUGO](https://gohugo.io/)

## 構築やり方（WSL2）

自分の環境：Windows10, WSL2

**大枠**

1. Github Pageを用意する
2. ローカルにHUGO入れる
3. pushしてHUGO×Github Pageでサイト公開

#### 1. Github Pageを用意する

公式がわかりやすく手順を書いてますので、それ通りに作成します。

[Github Pageの作成手順](https://docs.github.com/ja/pages/getting-started-with-github-pages/creating-a-github-pages-site)

#### 2. HUGO入れる

1. リポジトリをcloneしてローカル環境にブログ用のディレクトリを準備します。[HUGO Installation Linux](https://gohugo.io/installation/linux/)を参考に進めてください。私の環境はWSLのUbuntuです。DockerのイメージでHUGOをインストールすることもできましたが、Windows10のVmmemの問題が未だに解決しておらず、
   - 一般的なトラブルシューティング方法である.wslconfig設定ファイルの変更でも解決せず、まだ続いています。Windows 11にアップグレードすると解決するらしいです。Macが欲しい...
   - どこかのサイトでapt-getを使ってインストールするとバージョンが最新にならず、Themeによっては反映されないという噂を聞いたので、Goを直接WSLにインストールして動かすことにしました。

GoをインストールしてHUGOを起動する手順は[Build from source](https://gohugo.io/installation/linux/#build-from-source)に詳しく書かれています。

Goを扱ったことがなかったのですが、以下のパスを設定する必要があるんですね。
これせずに`hugo version`を実行してもバージョンが表示されず、ディレクトリ内でhugoコマンドを呼び出すことができませんでした。

```shell
$ export GOPATH=$HOME/go
$ export GOBIN=$GOPATH/bin
$ export PATH=$PATH:$GOPATH/bin
```

[Create a site](https://gohugo.io/getting-started/quick-start/#create-a-site)を参考にして、HUGOを立ち上げていきます。`hugo new site <xxxxxx>`コマンドを使用して、HUGOのファイルをリポジトリに追加します。ここでの`<xxxxxx>`はリポジトリ名です。必要に応じて`-f`フラグを使用してリポジトリに強制的に追加しました。

お好みのThemeを選んで`git submodule add https://<bbbbbb> themes/<bbbbbb>`を実行し、`hugo server`を起動すると、開発環境の構築は完了です。bbbbbbはTheme名など

あとは、`content/post`ディレクトリにMarkdownファイルを追加して記事を作成していきます。Themeによってやや異なるかもしれませんが、基本的な構成はThemeのドキュメントに記載されているはずです。

#### 3. pushしてHUGO×Github Pageでサイト公開

以下は、修正されたMarkdown形式の文章です。

hugoコマンドを使用すると、公開用のファイルが`./public`ディレクトリに生成されます。公開したいブログのMarkdownファイルのメタ情報には、`draft: false`と設定しておく必要があります。

HUGO × GitHub Pagesでホストする場合の手順がありました。[Host on GitHub](https://gohugo.io/hosting-and-deployment/hosting-on-github/)に記載されています。GitHub Actionsを使用して、プッシュのタイミングでビルドを行うような形です。

また、`hugo.toml`ファイルに`base_URL`などの設定を記述し、プッシュするとGitHub Actionsが作動し、自動的にビルドしてくれます。GitHub Actionsの経験がなかったので少し勉強になりました。


### 締め：ブログについて

久しぶりにブログ書いて、やっぱり文章書くの難しい。超読みずらい。chatgptに構成してもらったり、勉強しよう。