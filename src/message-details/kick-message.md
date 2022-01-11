# 4.2.8 Kick メッセージ

```
   Command:  KICK
Parameters:  <channel> <user> [<comment>]
```

KICK コマンドは，あるユーザをチャネルから強制的に排除するために使用します．これはチャネルから「追い出す」（forced PART）ことです．チャネルオペレータのみが他のユーザをチャネルから追い出すことができます．KICK メッセージを受信した各サーバは，それが有効であるかどうか（つまり，送信者が実際にチャネルオペレータであるかどうか）を，犠牲者をチャネルから追い出す前にチェックします．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_NOSUCHCHANNEL
    ERR_BADCHANMASK       ERR_CHANOPRIVSNEEDED
    ERR_NOTONCHANNEL
```

例：
```
KICK &Melbourne Matthew
        ; チャネル &Melbourne から Matthew をキックします．

KICK #Finnish John :Speaking English
        ; 英語で話すことを理由（コメント）に #Finnish から John をキックします．

:WiZ KICK #Finnish John
        ; チャネル #Finnish から John を削除するという Wiz からのキックメッセージ．
```

NOTE:
    KICK コマンドのパラメータを以下に拡張することが可能です．

```
<channel>{,<channel>} <user>{,<user>} [<comment>]
```
