# 4.2.7 招待メッセージ

```
   Command:  INVITE
Parameters:  <nickname> <channel>
```

INVITE メッセージは，ユーザをチャネルに招待するために使用されます．パラメータ \<nickname\> には，ターゲットチャネル \<channel\> に招待する人のニックネームを指定します．招待されるターゲットユーザが存在すること，または有効なチャネルであることは要求されません．招待専用チャネル（MODE +i）にユーザを招待するには，招待を送信するクライアントがそのチャネルのチャネルオペレータとして認識されている必要があります．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_NOSUCHNICK
    ERR_NOTONCHANNEL      ERR_USERONCHANNEL
    ERR_CHANOPRIVSNEEDED
    RPL_INVITING          RPL_AWAY
```

例：
```
:Angel INVITE Wiz #Dust      ; ユーザ Angel が WiZ をチャネル #Dust に招待しています．

INVITE Wiz #Twilight_Zone    ; WiZ を #Twilight_zone に招待するコマンド
```
