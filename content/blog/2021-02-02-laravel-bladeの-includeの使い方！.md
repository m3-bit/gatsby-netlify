---
title: Laravel Bladeの@includeの使い方！
date: 2021-02-02T09:04:28.206Z
description: ナビゲーション部分を別ファイルに切り出す
---
とりあえずレイアウトファイルを作って拡張できるようになれば、ごちゃごちゃしたコードは整理できるんですが、@include を使ってパーツをファイルを切り出すことでより管理がしやすくなります。

今回はナビゲーション部分を切り出すことにします。

viewsフォルダにincフォルダを作り、その中に nav.blade.php を追加します。

とりあえず[Bootstrapのこれ](view-source:https://getbootstrap.com/docs/4.0/examples/navbar-fixed/)を拝借してきましょう。

```html
<nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
  <a class="navbar-brand" href="#">Fixed navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarCollapse">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled" href="#">Disabled</a>
      </li>
    </ul>
    <form class="form-inline mt-2 mt-md-0">
      <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</nav>
```

これをメインレイアウトから引っ張ってきます。

```phtml
<body>
  @include(inc.nav)
</body>
```

こんな感じで使えます！