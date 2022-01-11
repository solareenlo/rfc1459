# 4.2.3.2 User モード

```
Parameters:  <nickname> {[+|-]|i|w|s|o}
```

ユーザモードは通常，クライアントが他者からどのように見られるか，またはクライアントがどのような「追加」メッセージを送信するかに影響する変更です．ユーザ MODE コマンドは，メッセージの送信者とパラメータとして与えられたニックネームの両方が同じである場合にのみ受け入れることができます．

使用可能なモードは以下の通りです．

```
    i - ユーザを非表示にします;
    s - サーバからのお知らせを受信するユーザをマークします;
    w - ユーザは，Wallops を受け取ります;
    o - オペレータフラグ．
```

後日，追加モードも用意される予定です．

ユーザが `+o` フラグを使用して自分自身をオペレータにしようとした場合，その試みは無視されるべきです．しかし，`-o` を使って自分自身をオペレータから外すことには何の制限もありません．

数値返信：
```
    ERR_NEEDMOREPARAMS      RPL_CHANNELMODEIS
    ERR_CHANOPRIVSNEEDED    ERR_NOSUCHNICK
    ERR_NOTONCHANNEL        ERR_KEYSET
    RPL_BANLIST             RPL_ENDOFBANLIST
    ERR_UNKNOWNMODE         ERR_NOSUCHCHANNEL

    ERR_USERSDONTMATCH      RPL_UMODEIS
    ERR_UMODEUNKNOWNFLAG
```

例：
```
Use of Channel Modes:

MODE #Finnish +im       ; #Finish のチャネルをモデレートされた「招待制」にします．

MODE #Finnish +o Kilroy ; チャネル #Finnish で Kilroy に ’chanop’ 権限を付与します．

MODE #Finnish +v Wiz    ; WiZに #Finnish で発言するのを許可します．

MODE #Fins -s           ; チャネル #Fins から ’secret’ フラグを削除します．

MODE #42 +k oulu        ; チャネルキーを "oulu" に設定します．

MODE #eu-opers +l 10    ; チャネルのユーザ数制限を 10 に設定します．

MODE &oulu +b           ; チャネルに設定されたバンマスクをリストアップします．

MODE &oulu +b !@*       ; すべてのユーザを参加させないようにします．

MODE &oulu +b !@*.edu   ; ホスト名が \*.edu に一致するユーザが参加できないようにします．

Use of user Modes:

:MODE WiZ -w            ; WiZ の WALLOPS メッセージの受信をオフにします．

:Angel MODE Angel +i    ; Angle からのメッセージを自分自身へ非表示にします．

MODE WiZ -o             ; WiZ をオペレータでなくします（オペレータの状態を解除する．）このコマンドの逆（"MODE WiZ +o"）は，OPER コマンドをバイパスしてしまうので，ユーザから許可されてはいけません．
```
