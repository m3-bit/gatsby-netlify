---
title: "cd: /usr/local/bin: No such file or directoryの解消方法！"
date: 2021-01-27T02:13:37.308Z
description: /usr/local/binに移動できないとき
---
初歩的だけど、意外と落とし穴だったのでメモ。

composerをrmで消そうと思ったら

```shell
-bash: cd: /usr/local/bin: No such file or directory
```

って言われた...
もちろん存在はしてる。

brewが使える前提にはなるんですが、下記コマンドを実行して直りました。

```shell
brew install ssh-copy-id
```