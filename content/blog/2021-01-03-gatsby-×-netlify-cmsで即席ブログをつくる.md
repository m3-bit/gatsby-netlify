---
title: Gatsby × Netlify CMSで即席ブログをつくる
date: 2021-01-02T23:32:56.547Z
description: GatsbyのブログコンテンツをNetlify CMSで管理する方法
---
CMSといえばWordPress一筋だったんですが、最近ヘッドレスCMSがどんどん増えてきました。\
やっぱりいろいろなフレームワークに乗り換えやすくなるという点で、こっちを選ぶ傾向が強くなってきました（個人的にやけど）。

最近Gatsby気に入っているので、今回はGatsbyとNetlify CMSを連携したブログを作りたいと思います。

## 環境

Mac BigSur

## 前提条件

* GitHubのアカウントを作っておく
* Netlify CMSのアカウントを作っておく
* Node.jsをインストールしておく
* 開発用エディタをインストールしておく（お好みで！自分はVS Code使ってます）

## Gatsbyのインストール

まずは下記コマンドをターミナルで実行し[gatsby-cli](https://www.npmjs.com/package/gatsby-cli)をインストールします。

```shell
npm install -g gatsby-cli
```

そしてプロジェクトを作るディレクトリに移動し、
プロジェクト名を指定してスターターブログをダウンロードしてきます。

```shell
cd <プロジェクトディレクトリ>
gatsby new <プロジェクト名> https://github.com/gatsbyjs/gatsby-starter-blog
```

プロジェクトに移動して、開発サーバを立ち上げます。

```shell
cd <プロジェクト名>
gatsby develop
```

http://localhost:8000

でサイトがスタートします。

## Netlify CMSプラグインをインストールする

ここにNetlify CMSのプラグインを追加します。

```shell
npm install netlify-cms-app gatsby-plugin-netlify-cms
```

でプラグインを追加

フォルダ **static** に新しいフォルダ **admin** を追加します。\
その下にファイル **config.yml** を作成します。

![gatsby](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.08.51.png?w=300 "folder_structure")

ここで何をするかというと、GitHubとの連携、フォルダディレクトリの指定、そしてコンテンツを作成するスキーマを生成していきます。\
後でカスタマイズできるので、ここではとりあえずコピっておけばOK。

```javascript
backend:
  name: git-gateway
  branch: master

media_folder: "static/img"
public_folder : "/img"

collections:
  - name: "Blog" 
    label: "Blog"
    folder: "content/blog"
    create: true
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}"
    editor:
      preview: true
    fields:
      - {label: "Title", name: "title", widget: "string"} 
      - {label: "Publish Date", name: "date", widget: "datetime"}
      - {label: "Description", name: "description", widget: "string"} 
      - {label: "Body", name: "body", widget: "markdown"}
```

そして**gatsby-config.js**に移動して、**\`gatsby-plugin-netlify-cms\`,**を追加します。

```javascript
    // 上にもいろいろ
    `gatsby-plugin-feed`,
    {
      resolve: `gatsby-plugin-manifest`,
      options: {
        name: `Gatsby Starter Blog`,
        short_name: `GatsbyJS`,
        start_url: `/`,
        background_color: `#ffffff`,
        theme_color: `#663399`,
        display: `minimal-ui`,
        icon: `content/assets/gatsby-icon.png`,
      },
    },
    `gatsby-plugin-react-helmet`,
    `gatsby-plugin-netlify-cms`, // ここに追加
    // this (optional) plugin enables Progressive Web App + Offline functionality
    // To learn more, visit: https://gatsby.dev/offline
    // `gatsby-plugin-offline`,
  ],
}
```

## GitHubでレポジトリを作る

<https://github.com/new> に移動して、Repository name（レポジトリ名）を入力して、公開設定Public（みんなに見られる）またはPrivate（自分だけ見れる）を選び、Create Repositoryボタンを押します。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.18.08.png?w=700 "Creating GitHub Repository")

生成されたURLをコピーしておきます。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.19.17.png?w=700 "GitHub Repository URL")

再びターミナルに戻り、gitレポジトリにプロジェクトをプッシュします。

まずは初期化して、

```shell
git init`
```

``\
`git add README.md // READMEの追加`\
`git commit -m "first commit" // first commitのコメントでコミット`\
masterブランチを作って、

```shell
git branch -M master
```

``\
`リモートレポジトリを追加`

```shell
git remote add origin "さっきのURL"
```

``\
`git push -u origin master // masterブランチへプッシュする`

更新してみると、ちゃんとプッシュできてます。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-5.33.11.png?w=700)

## Netlify CMSと連携！

Netlify CMSにログインし、**SitesからNew Sites from Git**ボタンをクリック。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.01.png?w=300)

そうするとGitHubへの認証が走ります。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.08.31.png?w=300)

レポジトリのアクセス許可画面になります。最低でも今から連携するレポジトリだけは許可しましょう。

![](https://m3bit.files.wordpress.com/2021/01/7_e8a8b1e58fafe383ace3839be3829ae981b8e381b5e38299.png?w=300)

こんな画面になるので接続するレポジトリを選ぶ。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.10.27.png?w=300)

なぜかブランチをmainにしてる、、\
けれどもmasterに変更しておきましょう。

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.11.36.png?w=300)

デプロイが始まります！

![](https://m3bit.files.wordpress.com/2021/01/screen-shot-2021-01-03-at-6.12.08.png?w=300)

git pull originする