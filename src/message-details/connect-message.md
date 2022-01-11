# 4.3.5 Connect メッセージ

```
   Command:  CONNECT
Parameters:  <target server> [<port> [<remote server>]]
```

CONNECT コマンドは，サーバが他のサーバとの新しい接続を直ちに確立しようとすることを強制するために使用することができます．CONNECT は特権的なコマンドであり，IRC オペレータのみが使用することができます．リモートサーバが指定された場合，そのサーバは `<target server>` と `<port>` に対して CONNECT を試みます．

数値返信：
```
    ERR_NOSUCHSERVER      ERR_NOPRIVILEGES
    ERR_NEEDMOREPARAMS
```

例：
```
CONNECT tolsun.oulu.fi
		; tolsun.oulu.fi へのサーバ接続を試みます．

:WiZ CONNECT eff.org 6667 csd.bu.edu
		; WiZ がサーバ eff.org と csd.bu.edu をポート 6667 で接続するために CONNECT を試みました．
```
