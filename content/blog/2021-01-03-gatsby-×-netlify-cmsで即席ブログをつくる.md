---
title: Gatsby × Netlify CMSで即席ブログをつくる
date: 2021-01-02T23:32:56.547Z
description: GatsbyのブログコンテンツをNetlify CMSで管理する方法
---
最近どのヘッドレスCMSがいいかいろいろ試してみてます。\
やっぱ早くて簡単なものがとっつきやすいですね。

まずは下記コマンドを実行します。

`npm install -g gatsby-cli`

そしてプロジェクトディレクトリに移動し、

gatsby new <名前> https://github.com/gatsbyjs/gatsby-starter-blog

cd <名前>

で移動して

gatsby develop

でサイトがスタートします。

npm i netlify-cms-app gatsby-plugin-netlify-cms

でプラグインを追加

static > adminフォルダ > config.ymlを作成します。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.08.51.png?w=200)

ソースはこんな感じ

backend: name: git-gateway branch: master\
media_folder: "static/img"public_folder : "/img"\
collections: - name: "Blog" label: "Blog" folder: "content/blog" create: true slug: "{{year}}-{{month}}-{{day}}-{{slug}}" editor: preview: false fields: - {label: "Title", name: "title", widget: "string"} - {label: "Publish Date", name: "date", widget: "datetime"} - {label: "Description", name: "description", widget: "string"} - {label: "Body", name: "body", widget: "markdown"}

そしてgatsby-config.jsに移動して、\`gatsby-plugin-netlify-cms\`,を追加します。

先にGitHubでレポジトリを作りましょう！

https://github.com/new

に移動して、Repository name（レポジトリ名）を入力して、PublicまたはPrivateを選び、Create Repositoryボタンを押します。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.18.08.png?w=300)


URLをコピっておきます。


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.19.17.png?w=300)

そしてターミナルに戻って、gitレポジトリにプッシュします。

git init\
git add README.md\
git commit -m "first commit"\
git brach -M main\
git remote add origin "さっきのURL"\
git push -u origin main

更新してみると、ふむふむできております。


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.33.11.png?w=300)


netlifyと接続！

netlifyにログインして（アカウントを持っていない場合は作成してください）


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.01.png?w=300)


そうするとGitHubへの認証が走ります。


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.31.png?w=300)


レポジトリを選ぶ。


![](https://m3bit.files.wordpress.com/2021/01/7_e8a8b1e58fafe383ace3839be3829ae981b8e381b5e38299.png?w=300)


こんな画面になるので接続するレポジトリを選ぶ。


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.10.27.png?w=300)


なぜブランチmainにしたんやろ、、皆さんはmasterに変更しておきましょう。


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.11.36.png?w=300)


デプロイが始まる


![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.12.08.png?w=300)


git pull originする

