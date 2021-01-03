---
title: Gatsby × Netlify CMSで即席ブログをつくる
date: 2021-01-02T23:32:56.547Z
description: aaaa
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

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

でサイトがスタートします。

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

npm i netlify-cms-app gatsby-plugin-netlify-cms

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

でプラグインを追加

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

static > adminフォルダ > config.ymlを作成します。

<!-- /wp:paragraph -->

<!-- wp:image {"id":997,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.08.51.png?w=606)

<!-- /wp:image -->

<!-- wp:paragraph -->

ソースはこんな感じ

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

backend: name: git-gateway branch: master\
media_folder: "static/img"public_folder : "/img"\
collections: - name: "Blog" label: "Blog" folder: "content/blog" create: true slug: "{{year}}-{{month}}-{{day}}-{{slug}}" editor: preview: false fields: - {label: "Title", name: "title", widget: "string"} - {label: "Publish Date", name: "date", widget: "datetime"} - {label: "Description", name: "description", widget: "string"} - {label: "Body", name: "body", widget: "markdown"}

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

そしてgatsby-config.jsに移動して、\`gatsby-plugin-netlify-cms\`,を追加します。

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

先にGitHubでレポジトリを作りましょう！

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

https://github.com/new

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

に移動して、Repository name（レポジトリ名）を入力して、PublicまたはPrivateを選び、Create Repositoryボタンを押します。

<!-- /wp:paragraph -->

<!-- wp:image {"id":999,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.18.08.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

URLをコピっておきます。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1002,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.19.17.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

そしてターミナルに戻って、gitレポジトリにプッシュします。

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

git init\
git add README.md\
git commit -m "first commit"\
git brach -M main\
git remote add origin "さっきのURL"\
git push -u origin main

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

更新してみると、ふむふむできております。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1003,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.33.11.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

netlifyと接続！

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

netlifyにログインして（アカウントを持っていない場合は作成してください）

<!-- /wp:paragraph -->

<!-- wp:image {"id":1010,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.01.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

そうするとGitHubへの認証が走ります。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1012,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.31.png?w=783)

<!-- /wp:image -->

<!-- wp:paragraph -->

レポジトリを選ぶ。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1014,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/7_e8a8b1e58fafe383ace3839be3829ae981b8e381b5e38299.png?w=743)

<!-- /wp:image -->

<!-- wp:paragraph -->

こんな画面になるので接続するレポジトリを選ぶ。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1016,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.10.27.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

なぜブランチmainにしたんやろ、、皆さんはmasterに変更しておきましょう。

<!-- /wp:paragraph -->

<!-- wp:image {"id":1018,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.11.36.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

デプロイが始まる

<!-- /wp:paragraph -->

<!-- wp:image {"id":1020,"sizeSlug":"large","linkDestination":"none"} -->

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.12.08.png?w=1024)

<!-- /wp:image -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

git pull originする

<!-- /wp:paragraph -->