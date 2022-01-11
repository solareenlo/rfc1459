# 4.6.3 Pong メッセージ

```
Command   :  PONG
Parameters:  <daemon> [<daemon2>]
```

PONG メッセージは，Ping メッセージに対する返信です．パラメータ `<daemon2>` が指定された場合，このメッセージは指定されたデーモンに転送されなければなりません．`<daemon>` パラメータには，PING メッセージに応答し，このメッセージを生成したデーモンの名前を指定します．

数値返信：
```
    ERR_NOORIGIN    ERR_NOSUCHSERVER
```

例：
```
PONG csd.bu.edu tolsun.oulu.fi    ; csd.bu.edu から tolsun.oulu.fi への PONG メッセージ
```
