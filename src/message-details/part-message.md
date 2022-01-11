# 4.2.2 パートメッセージ

```
   Command:  PART
Parameters:  <channel>{,<channel>}
```

PART メッセージは，メッセージを送信したクライアントを，パラメータ文字列で指定されたすべてのチャネルのアクティブユーザ一覧から削除します．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_NOSUCHCHANNEL
    ERR_NOTONCHANNEL
```

例：
```
PART #twilight_zone    ; チャネル "#twilight_zone" を離脱します．

PART #oz-ops,&group5   ; "&group5" と "#oz-ops" の両方のチャネルを離脱します．
```
