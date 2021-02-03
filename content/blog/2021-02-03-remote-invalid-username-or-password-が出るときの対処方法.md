---
title: "remote: Invalid username or password.が出るときの対処方法"
date: 2021-02-03T03:19:38.101Z
description: SourceTreeでプッシュできないとき
---
SourceTreeで久々にプッシュしようとしたら、こんなエラーで怒られたので、そのときの対処法。\
自分の場合は、使わなくなったGitユーザを削除していて、それがデフォルトのログインアカウントになっていたようでした。

まずはFinderで下記フォルダを開く。

**~Library > Application Support > SourceTree**

**ユーザ名@STAuth-github.com**というファイルがあるので、これを削除。

次に**Keychain Access**を開いて、sourcetreeの認証情報を削除。

あとはSourceTreeのデフォルトアカウントに登録していたのでこれも削除。