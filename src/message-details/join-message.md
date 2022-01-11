# 4.2.1 参加メッセージ

```
   Command:  JOIN
Parameters:  <channel>{,<channel>} [<key>{,<key>}]
```

JOIN コマンドは，クライアントが特定のチャネルのリスニングを開始するために使用されます．クライアントがチャネルに参加できるかどうかは，クライアントが接続しているサーバのみが確認します．他のサーバは，他のサーバからチャネルを受信すると，自動的にユーザをチャネルに追加します．これに影響する条件は以下の通りです．

1. チャネルが招待制である場合，ユーザは招待されていなければなりません．
2. ユーザのニックネーム/ユーザ名/ホスト名は，アクティブな禁止事項にマッチしてはいけません．
3. 正しいキー(パスワード)が設定されている場合は，それを入力しなければなりません．

これらについては，MODE コマンドで詳しく説明します（詳細は[4.2.3 モードメッセージ](./mode-message.md)の章を参照してください）．

ユーザがチャネルに参加すると，そのチャネルに影響を与えるサーバが受け取るすべてのコマンドに関する通知を受け取ります．これには，MODE，KICK，PART，QUIT や，もちろん PRIVMSG/NOTICE が含まれます．JOIN コマンドは，各サーバがチャネルに参加しているユーザをどこで見つけることができるかを知るために，すべてのサーバにブロードキャストされる必要があります．これにより，PRIVMSG/NOTICE メッセージのチャネルへの最適な配信が可能になります．

JOIN が成功すると，ユーザにチャネルのトピック（RPL_TOPIC を使用）とチャネルに参加しているユーザのリスト（RPL_NAMREPLY を使用）が送られますが，これには参加しているユーザを含める必要があります．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_BANNEDFROMCHAN
    ERR_INVITEONLYCHAN    ERR_BADCHANNELKEY
    ERR_CHANNELISFULL     ERR_BADCHANMASK
    ERR_NOSUCHCHANNEL     ERR_TOOMANYCHANNELS
    RPL_TOPIC
```

例：
```
JOIN #foobar                ; チャネル #foobar に参加します．

JOIN &foo fubar             ; "fubar" をキーにチャネル &foo に参加します．

JOIN #foo,&bar fubar        ; チャネル #foo にキー "fubar" で，&bar にキー無しで参加します．

JOIN #foo,#bar fubar,foobar ; キー "fubar" を使ってチャネル #foo に参加し，キー "foobar" を使ってチャネル #bar に参加します．

JOIN #foo,#bar              ; チャネル #foo と #bar に参加します．

:WiZ JOIN #Twilight_zone    ; WiZ からの JOIN メッセージ
```
