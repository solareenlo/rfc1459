# 4.4.1 Private メッセージ

```
   Command:  PRIVMSG
Parameters:  <receiver>{,<receiver>} <text to be sent>
```

PRIVMSG は，ユーザ間のプライベートメッセージの送信に使用されます．`<receiver>` には，メッセージの受信者のニックネームを指定します．`<receiver>` はカンマで区切られた名前またはチャネルのリストでもかまいません．

`<receiver>` パラメータには，ホストマスク（`#mask`）またはサーバマスク（`$mask`）を指定することもできます．どちらの場合も，サーバはこのマスクに一致するサーバやホストを持つ人にのみ PRIVMSG を送ります．マスクには少なくとも1つの `.` が必要で，最後の `.` の後にはワイルドカードを使用しないでください．この条件は，`#*` や `$*` にメッセージを送ると，すべてのユーザにブロードキャストされてしまうのを防ぐためにあります．経験上，これは責任を持って適切に使われるよりも悪用されることが多いです． ワイルドカードとは，`*` および `?` 文字のことです．この PRIVMSG コマンドの拡張は，オペレータのみが使用できます．

数値返信：
```
    ERR_NORECIPIENT         ERR_NOTEXTTOSEND
    ERR_CANNOTSENDTOCHAN    ERR_NOTOPLEVEL
    ERR_WILDTOPLEVEL        ERR_TOOMANYTARGETS
    ERR_NOSUCHNICK
    RPL_AWAY
```

例：
```
:Angel PRIVMSG Wiz :Hello are you receiving this message ?
        ; Angel からの Wiz へのメッセージ
PRIVMSG Angel :yes I’m receiving it !receiving it !’u>(768u+1n) .br
        ; Angel へのメッセージ
PRIVMSG jto@tolsun.oulu.fi :Hello !
        ; サーバ tolsun.oulu.fi のユーザ名 "jto" のクライアントへのメッセージ．
PRIVMSG $*.fi :Server tolsun.oulu.fi rebooting.
        ; *.fi に一致する名前を持つサーバ上のすべての人へのメッセージ．
PRIVMSG #*.edu :NSFNet is undergoing work, expect interruptions
        ; ホスト名が *.edu に一致するホストから来たすべてのユーザへのメッセージ．
```
