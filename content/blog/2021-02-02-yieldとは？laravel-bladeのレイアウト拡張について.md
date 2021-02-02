---
title: "@yieldとは？Laravel Bladeのレイアウト拡張について"
date: 2021-02-02T05:36:14.805Z
description: "@yieldの使い方"
---
Webサイトなどでページをどんどん追加していくと、headタグとか同じコードをコピペしたファイルがどんどん増えてきます。

要は冗長なコードが増えるわけです（自分で言いながら耳が痛い(´·ω·`)）。

LaravelではBladeをテンプレートエンジンとして使っているので、こういったレイアウトの拡張がめちゃくちゃ簡単にできます。
@yieldはそのBladeで使う記述方法ということで、使い方を見ていきましょう！

例えばこういうファイルがあります。

```phtml
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>{{config('app.name')}}</title>
    </head>
    <body>
        <h1>トップページ</h1>
        <p>Lorem Ipsum</p>
    </body>
</html>
```

おそらく、別のページを追加するとなると、bodyタグの部分だけ変更してあとは一緒にしたいはずです。ということで、その場合に親ページとなるレイアウトを作ります。

```phtml
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>{{config('app.name')}}</title>
    </head>
    <body>
        @yield('content')
    </body>
</html>
```

出てきました、**@yield**です。
これから拡張した子ファイルを作って、そこで定義するコンテンツの値がこの@yieldに挿入されます。

ということで、子ファイルの例を見てみましょう。

```phtml
@extends('layouts.app')

@section('content')
    <h1>トップページ</h1>
    <p>Lorem Ipsum</p>
@endsection
```

@extendsはレイアウトファイルの宣言です。ここでは、layoutsフォルダのapp.blade.phpを拡張するという宣言になっています。

そして@section('content')から@endsectionまでが、先ほどの@yield('content')に入る内容になります。要するに、一番上の例と全く同じアウトプットになるということです。

というわけで、上記の例のように、コンテンツの部分だけ変更するだけ。
こんな感じでBladeでは効率的な記述にすることができます。