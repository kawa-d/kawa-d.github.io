---
title: HugoとGithub Pageでブログ用サイト作ってみました
description: 継続できるのか！？
date: 2023-07-09 00:00:00+0000
draft: false
# image: cover.jpg
# categories:
#     - Example Category
# tags:
#     - Example Tag
---

## 気まぐれ

気まぐれで色々初めてしまう癖があり、継続できないのが毎度のパターンなんですが、最近はそれを反省して継続を意識するようになりました。
がんばって１年は続けていきたいです。
仕事は情シスなので、情シス関連の技術ブログをメインに書いていきたいですが、「継続」ってのがサブテーマなので、ただの日記などジャンルは幅広くしてネタが尽きないようにしたいです。

## Github Page
タイトル通りHugoとGithub Pageでブログ用サイト作ってみました。
Github Pageは静的サイトをホストできるところです。Githubアカウント持ってたら無料で使えます。広告も貼れるらしいです。
[Github Page](https://docs.github.com/ja/pages/getting-started-with-github-pages/about-github-pages)

## HUGO

HUGOは静的サイトジェネレーターとかいう、いい感じにブログっぽい見た目をサクッと構築してくれるフレームワーク的なやつです。
HUGO > Themesってのがあって、おしゃれでセンスのあるデザイナーさんたちが色んなフレームワークを作ってます。お気に入りを見つけて、cloneして、HUGOにいれれば使えるようになります。Themesを選ぶとそのGithubのリポジトリに飛ぶんですが、ドキュメントが揃ってて入れやすいイメージです。
自分が使用してるのはStackってやつです。

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

1.で作ったリポジトリをcloneしてローカル環境にブログ用のディレクトリを用意します。
[HUGO Installation Linux](https://gohugo.io/installation/linux/)を見ながら入れていきます。
自分の環境はWSLのUbuntuです。DockerのimageでHUGO入れてもよかったんですが、未だにwindows10のVmmem暴走する問題に悩まされていて、
- よくあるトラブルシュートで.wslconfig設定ファイルをいじっても治らずのままです。win11にすると治るらしい？Macがほしい。
- どこかのサイトでapt-getでやるとバージョンが最新にならずThemeによっては反映されないという噂を聞いたため、もうGoを直接wslにいれて動かそうという流れになりました。

Goを入れてHUGO立ち上げる手順は[Build from source](https://gohugo.io/installation/linux/#build-from-source)に載ってます。

Goを扱ったことがなかったのですが、下記のPATHを設定しないといけないようで、`hugo version`でversionが出ず、ディレクトリ内でhugoコマンド呼び出せなかったです。

```shell
$ export GOPATH=$HOME/go
$ export GOBIN=$GOPATH/bin
$ export PATH=$PATH:$GOPATH/bin
```
[Create a site](https://gohugo.io/getting-started/quick-start/#create-a-site) を見ながら、HUGOを立ち上げていきます。
`hugo new site <xxxxxx>`で、HUGOのファイルをリポジトリに入れます。xxxxxxの部分はリポジトリ名で、-fだったかでforceしながらリポジトリに強制的にいれました。

`git submodule add https://<xxxxxx> themes/<xxxxxx>`で好きなThemeいれて、`hugo server`で立ち上げたら、開発環境構築終わりです。

あとは、content/post配下に.mdファイルいれて記事つくります。この辺の構成はThemeによって若干違いますが、Themeのドキュメントに基本的には書いてあるのでそれに沿ってやっていきます。

#### 3. pushしてHUGO×Github Pageでサイト公開

HUGOがGithub Pageにあげる場合、Actions使って、プッシュのタイミングでビルドするような手順を[Host on GitHub](https://gohugo.io/hosting-and-deployment/hosting-on-github/)に書いてたので、その通りにしていく。



