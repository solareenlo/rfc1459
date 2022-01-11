# 5.4 Summon メッセージ

```
Command   :  SUMMON
Parameters:  <user> [<server>]
```

SUMMON コマンドは，IRC サーバを実行しているホストにいるユーザに，IRC に参加してくださいというメッセージを送るために使用することができます．このメッセージは，ターゲットサーバが (a) SUMMON を有効にしていて， (b) ユーザがログインしていて， (c) サーバプロセスがユーザの tty（または同様のもの）に書き込める場合にのみ送信されます．

`<server>` パラメータを指定しない場合，クライアントが接続しているサーバから `<user>` を呼び出そうとするものとします．

サーバで SUMMON が有効でない場合，ERR_SUMMONDISABLED の数値を返し，SUMMON メッセージを以降に渡さなければなりません．

数値返信：
```
    ERR_NORECIPIENT    ERR_FILEERROR
    ERR_NOLOGIN        ERR_NOSUCHSERVER
    RPL_SUMMONING
```

例：
```
SUMMON jto                   ; サーバのホストでユーザ jto を召喚します．
SUMMON jto tolsun.oulu.fi    ; "tolsun.ulu.fi" という名前のサーバが稼働しているホストで，ユーザ jto を召喚します．
```
