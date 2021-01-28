---
title: 【Laravel 8.x】コントローラーをArtisanで作る
date: 2021-01-28T02:31:12.990Z
description: コントローラーを作る
---
## Artisanでコントローラーを作る

コントローラーを作るコマンド↓\
最後はコントローラー名で、ここではPagesControllerという名前でファイルが作られます。

```shell
php artisan make:controller PagesController
```

`Controller created successfully.`

と出ればOK。**app** → **Http** → **Controllers** の中に**PagesController**がひっそりいてるはずです。\
もちろん手動で作ってもいいんですが、名前空間とかを自動で生成してくれるのでArtisan使う方が効率的です。

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class PagesController extends Controller
{
    //
}
```

**index**という関数を作っておきます。\
**views** → **pages**(これは自分で作った) の中に **m3-bit.blade.php**というViewがあるとして、これを呼び出す関数にします。

```php
    public function index() {
        return view('pages.m3-bit');
    }
```

web.phpに戻って、まずPagesControllerを使う宣言をします。
ちなみに、前のバージョンだったらこの作業要らんかったっぽい。

```php
use App\Http\Controllers\PagesController;
```

そして、**/pages**にアクセスされたときに、**index**関数を呼び出して、**m3-bit.blade.php** のビューを表示できるようになります。

```php
Route::get('/pages', [PagesController::class, 'index']);
```

こうやってURIとViewを定義するfunctionを増やしていけば、ルーティング管理もラクになります。