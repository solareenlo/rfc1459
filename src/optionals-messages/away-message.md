# 5.1 Away メッセージ
```
Command   :  AWAY
Parameters:  [message]
```

AWAY メッセージにより，クライアントは自分宛の PRIVMSG コマンド（自分がいるチャネル宛ではない）に対して，自動返信文字列を設定することができます．自動応答は，PRIVMSG コマンドを送信するクライアントに対してサーバから送信されます．返信するサーバは，送信側クライアントが接続されているサーバのみです．

AWAY メッセージは1つのパラメータで使用する（AWAY メッセージを設定する）か，パラメータなしで使用する（AWAY メッセージを削除する）かを選択します．

数値返信：
```
    RPL_UNAWAY    RPL_NOWAWAY
```

例：
```
AWAY :Gone to lunch. Back in 5    ; AWAY メッセージを "Gone to lunch.  Back in 5" に設定します．
:WiZ AWAY                         ; WiZ を AWAY としてマーク解除する．
```
