# 4.3.6 Trace メッセージ

```
   Command:  TRACE
Parameters:  [<server>]
```

TRACE コマンドは，特定のサーバへの経路を検索するために使用されます．このメッセージを処理する各サーバは，パススルーリンクであることを示す応答を送信して送信者に伝える必要があり，"traceroute" を使用して得られるのと同様の応答の連鎖を形成します．この応答を送り返した後，指定されたサーバに到達するまで，次のサーバに TRACE メッセージを送信しなければなりません．`<server>` パラメータが省略された場合，TRACE コマンドは，現在のサーバがどのサーバに直接接続しているかを送信者に伝えるメッセージを送信することが推奨されます．

`<server>` で指定された送信先が実際のサーバである場合，送信先サーバは接続されているすべてのサーバとユーザを報告する必要がありますが，オペレータのみがユーザの存在を確認することを許可されます．`<server>` で指定された宛先がニックネームの場合，そのニックネームに対する応答のみが返されます．

数値返信：
```
    ERR_NOSUCHSERVER

TRACE メッセージが他のサーバに向けられた場合，すべての中間サーバは RPL_TRACELINK 応答を返し，TRACE がそれを通過したことと次の行き先を示す必要があります．

    RPL_TRACELINK
TRACE 応答は，以下の数値応答からいくつでも構成することができます．

    RPL_TRACECONNECTING    RPL_TRACEHANDSHAKE
    RPL_TRACEUNKNOWN       RPL_TRACEOPERATOR
    RPL_TRACEUSER          RPL_TRACESERVER
    RPL_TRACESERVICE       RPL_TRACENEWTYPE
    RPL_TRACECLASS
```

例：
```
TRACE *.oulu.fi         ; *.oulu.fi に一致するサーバへの TRACE．

:WiZ TRACE AngelDust    ; WiZ が AngelDust のニックネームに対して発行した TRACE．
```
