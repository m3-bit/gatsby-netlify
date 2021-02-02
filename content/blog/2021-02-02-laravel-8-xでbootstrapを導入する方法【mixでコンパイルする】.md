---
title: Laravel 8.xでBootstrapを導入する方法【Mixでコンパイルする】
date: 2021-02-02T07:29:20.597Z
description: Sassなどのコンパイルアセットなどなど
---
Bootstrapの導入がちょっと変わってたのでメモ。

まずは**laravel/ui**というコンポーネントをインストールします。ここにbootstrapが入ってます。

```shell
composer require laravel/ui
```

Artisanで下記コマンドを実行すると、bootstrapフォルダが作られます。

```shell
php artisan ui bootstrap
```

ここで**npm install**を実行すると、**node_modules**フォルダが作られます。

```shell
npm install
```

で、下記コマンドを実行します。

```shell
npm run dev
```

これでOKかと思いきや

`Additional dependencies must be installed. This will only take a moment.`

と言われます。

`Finished. Please run Mix again.`

ということで、もう一度実行することになります。

```shell
npm run dev
```

2度目に**Compiled Successfully**という画面が出ました。これで準備OK。

呼び出し方はこんな感じ。

```phtml
<link rel="stylesheet" href="{{asset('/css/app.css')}}">
```

では、ちょっとsassファイルをいじってみましょう。

```sass
$body-bg: red;　// 例えば
```

これ、変更を保存するだけだと反映されません。必ず**npm run dev**でコンパイルする必要があります。これが面倒な場合は、**npm run watch**で監視させておけば自動的にリコンパイルしてくれます。