---
title: 【初心者向け！】WindowsでのComposerインストール方法
date: 2021-01-26T01:50:25.455Z
description: Composerインストール方法
---
パッケージ管理ツールの王道、[Composer](https://getcomposer.org/)のインストール方法をご紹介します٩( 'ω' )و

## 1. インストーラーをダウンロードする

まずは[ダウンロードページ](https://getcomposer.org/download/)に行って、Composer-Setup.exeをクリックしてインストーラーをダウンロードします。

![composer_windows_installer](/img/composer1.png "composer_setup_1")



## 2. インストーラーを起動する

ダウンロードが終わったら、インストーラーを開きます。

Developer Modeというチェックボックスがありますが、これをチェックするとアンインストーラーがパッケージに含まれません。

基本的にはチェックなしで進んでOKです。Nextをクリックします。

![composer_installation_options](/img/composer2.png "composer_setup_2")

## 3. PHPのパスを指定する

次は使用するPHPのパスを指定します。自動的にパスを指定してくれますが、複数インストールしてたりする場合はここで変更して、Nextで進みます。

![composer_settings_check](/img/composer3.png "composer_install_3")

## 4. プロキシの設定

次にプロキシの設定です。プロキシを経由する場合はチェックして、Nextをクリック。

![composer_proxy_settings](/img/composer4.png "composer_setup_4")

## 5. 設定の確認

最終確認画面です。PHPバージョンとPHPのパス、プロキシ設定が表示されているので、ミスってる場合は戻って設定し直しましょう。

問題なければInstallをクリックするとインストールが始まります。

![composer_ready_to_install](/img/composer5.png "composer_setup_5")

## 6. インストール完了

インストールが完了したら、下記の画面になります。続けてドキュメンテーションを開きたい場合は、チェックボックスにチェックを入れてFinishを押します。

![completing composer setup](/img/composer6.png "composer_setup_6")

以上で、Composerのセットアップは完了です！！

コマンドプロンプトで

`composer -v`

が使えるか確認してみてください！👍