---
title: 【Laravel 8.x】コントローラーをArtisanで作る
date: 2021-01-28T02:31:12.990Z
description: コントローラーを作る
---
## Artisanでコントローラーを作る

コントローラーを作るコマンド↓

```shell
php artisan make:controller PagesController
```

ちなみに最後がコントローラー名で、ここではPagesControllerという名前でファイルが作られます。

`Controller created successfully.`

と出ればOK。**app** → **Http** → **Controllers** の中に**PagesController**がひっそりいてるはずです。\
もちろんファイルは手動で作ってもいいんですが、名前空間とかを自動で生成してくれるのでArtisan使って作る方が効率的です。

こんなコントローラーが生成されます。

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class PagesController extends Controller
{
    //
}
```

ここには**index**という関数を作っておきます。\
**views** フォルダ → **pages**(これは自分で作った) フォルダの中に **m3-bit.blade.php**というViewがあるとして、これを呼び出す関数にします。

```php
    public function index() {
        return view('pages.m3-bit');
    }
```

**web.php**に戻って、まず**PagesController**を使う宣言をします。

```php
use App\Http\Controllers\PagesController;
```

そして、**/pages**にアクセスされたときに、**index**関数を呼び出して、**m3-bit.blade.php** のビューを表示できるようにします。以上！！

```php
Route::get('/pages', [PagesController::class, 'index']);
```

こうやってURIとViewを定義するfunctionを増やしていけば、ルーティング管理もラクになります。