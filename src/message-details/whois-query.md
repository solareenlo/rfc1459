# 4.5.2 Whois クエリ

```
   Command:  WHOIS
Parameters:  [<server>] <nickmask>[,<nickmask>[,...]]
```

このメッセージは，特定のユーザに関する情報を問い合わせるために使用されます．サーバはこのメッセージに対して，ニックネームと一致する各ユーザの異なるステータスを示すいくつかの数値メッセージを返します（あなたがそれらを見る権利がある場合）．`<nickmask>` にワイルドカードが指定されていない場合は，そのニックネームに関する，閲覧可能なすべての情報が表示されます．カンマ（`,`）で区切ったニックネームのリストを指定することもできます．

後者は，特定のサーバに問い合わせを行うものです．ローカルサーバ（つまり，ユーザが直接接続しているサーバ）だけがその情報を知っており，他のすべてはグローバルに知られているので，問題のユーザがどれくらいアイドル状態であったかを知りたい場合に有用です．

数値返信：
```
    ERR_NOSUCHSERVER     ERR_NONICKNAMEGIVEN
    RPL_WHOISUSER        RPL_WHOISCHANNELS
    RPL_WHOISCHANNELS    RPL_WHOISSERVER
    RPL_AWAY             RPL_WHOISOPERATOR
    RPL_WHOISIDLE        ERR_NOSUCHNICK
    RPL_ENDOFWHOIS
```

例：
```
WHOIS wiz                 ; nick WiZ に関する利用可能なユーザ情報を返します．
WHOIS eff.org trillian    ; trillian に関するユーザ情報をサーバ eff.org に問い合わせます．
```
