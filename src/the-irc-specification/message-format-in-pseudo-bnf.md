# 2.3.1 `疑似` BNF によるメッセージ形式

プロトコルメッセージは，オクテットの連続したストリームから抽出されなければなりません．現在の解決策は，`CR` と `LF` という2つの文字をメッセージのセパレータとして指定することです．空のメッセージは黙って無視されるので，メッセージ間で `CR-LF` のシーケンスが余分な問題なく使用できるようになります．

抽出されたメッセージは，`<prefix>`，`<command>` という要素と，`<middle>` または `<trailing>` のどちらかの要素でマッチするパラメータのリストに解析されます．

これを BNF で表現すると
```
<message>  ::= [’:’ <prefix> <SPACE> ] <command> <params> <crlf>
<prefix>   ::= <servername> | <nick> [ ’!’ <user> ] [ ’@’ <host> ]
<command>  ::= <letter> { <letter> } | <number> <number> <number>
<SPACE>    ::= ’ ’ { ’ ’ }
<params>   ::= <SPACE> [ ’:’ <trailing> | <middle> <params> ]
<middle>   ::= <SPACE，NUL，CR，LFを含まない，*空でない*オクテットのシーケンス． その最初の文字が’:’であってはならない．>
<trailing> ::= <NUL，CR，LF を含まない，任意の（場合によっては*空白の*）オクテット列>
<crlf>     ::= CR LF
```

NOTES:
1) `<SPACE>` は，スペース文字（`0x20`）のみで構成されます．特に，TABULATION と他のすべての制御文字は非空白文字とみなされます．
2) パラメータリスト抽出後，`<middle>` でマッチングしても `<trailing>` でマッチングしても，すべてのパラメータは等しくなります．`<trailing>` は，パラメータ内の SPACE を許容するための構文上のトリックに過ぎません．
3) パラメータ文字列に CR と LF が出現しないのは，メッセージのフレームワークのせいです．これは後で変更されるかもしれません．
4) NUL 文字はメッセージのフレーム化において特別なものではなく，基本的にはパラメータの内部で終わる可能性がありますが，通常の C の文字列処理において余分な複雑さを引き起こすため，この文字は使用できません．したがって，NUL はメッセージの中では許されません．
5) 最後のパラメータには，空文字列を指定することができます．
6) 拡張プレフィックス（[`! <user>`] [`@ <host>`]）の使用は，サーバ間通信では使用してはならず，サーバからクライアントへのメッセージに限り，追加の問い合わせを必要とせずにメッセージの送信元に関するより有用な情報をクライアントに提供するために意図されています．

ほとんどのプロトコルメッセージは，リスト内の位置によって，抽出されたパラメータ文字列の追加のセマンティクスとシンタックスを指定しています．例えば，多くのサーバコマンドは，コマンドの後の最初のパラメータがターゲットのリストであると仮定し，これを記述することができます．

```
<target>     ::= <to> [ "," <target> ]
<to>         ::= <channel> | <user> ’@’ <servername> | <nick> | <mask>
<channel>    ::= (’#’ | ’&’) <chstring>
<servername> ::= <host>
<host>       ::= see RFC 952 [DNS:4] for details on allowed hostnames
<nick>       ::= <letter> { <letter> | <number> | <special> }
<mask>       ::= (’#’ | ’$’) <chstring>
<chstring>   ::= <any 8bit code except SPACE, BELL, NUL, CR, LF and comma (’,’)>
```

その他のパラメータ構文は以下の通りです．

```
<user>     ::= <nonwhite> { <nonwhite> }
<letter>   ::= ’a’ ... ’z’ | ’A’ ... ’Z’
<number>   ::= ’0’ ... ’9’
<special>  ::= ’-’ | ’[’ | ’]’ | ’\’ | ’‘’ | ’^’ | ’{’ | ’}’
<nonwhite> ::= <any 8bit code except SPACE (0x20), NUL (0x0), CR (0xd), and LF (0xa)>
```
