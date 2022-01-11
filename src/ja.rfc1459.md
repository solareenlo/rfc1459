## 6. REPLIES
以下は，上記のコマンドに応答して生成される数値応答のリストです．各数値は，番号，名前，返信文字列で示されます．

### 6.1 Error Replies.
```
401    ERR_NOSUCHNICK
           "<nickname> :No such nick/channel"
       - コマンドに与えられたニックネームパラメータが現在未使用であることを示すために使用されます．

402    ERR_NOSUCHSERVER
           "<server name> :No such server"
       - 指定されたサーバ名が現在存在しないことを示すために使用されます．

403    ERR_NOSUCHCHANNEL
           "<channel name> :No such channel"
       - 与えられたチャネル名が無効であることを示すために使用されます．

404    ERR_CANNOTSENDTOCHAN
           "<channel name> :Cannot send to channel"
       - (a) モード +n が設定されているチャネルにいない，または (b) モード +m が設定されているチャネルのチャノップ (またはモード +v) でないユーザが，そのチャネルに PRIVMSG メッセージを送信しようとしたときに送信されます．

405    ERR_TOOMANYCHANNELS
           "<channel name> :You have joined too many channels"
       - ユーザが許可された最大数のチャネルに参加し，別のチャネルに参加しようとしたときに送信されます．

406    ERR_WASNOSUCHNICK
           "<nickname> :There was no such nickname"
       - WHOWAS により，そのニックネームの履歴情報がないことを示すために返されます．

407    ERR_TOOMANYTARGETS
           "<target> :Duplicate recipients. No message delivered"
       - PRIVMSG/NOTICE を user@host の宛先フォーマットで，user@host が複数存在する場合に送信しようとしたクライアントに返されます．

409    ERR_NOORIGIN
           ":No origin specified"
       - PING または PONG メッセージに originator パラメータがない．これらのコマンドは有効な接頭辞がないと動作しないため，必須です．

411    ERR_NORECIPIENT
           ":No recipient given (<command>)"

412    ERR_NOTEXTTOSEND
           ":No text to send"

413    ERR_NOTOPLEVEL
           "<mask> :No toplevel domain specified"

414    ERR_WILDTOPLEVEL
           "<mask> :Wildcard in toplevel domain"
       - 412 - 414は，何らかの理由でメッセージが届かなかったことを示すために PRIVMSG が返すものです．
         ERR_NOTOPLEVEL と ERR_WILDTOPLEVEL は "PRIVMSG $<server>" または "PRIVMSG #<host>" を不正に使用しようとしたときに返されるエラーです．

421    ERR_UNKNOWNCOMMAND
           "<command> :Unknown command"
       - 送信されたコマンドがサーバによって不明であることを示すために，登録されたクライアントに返されます．

422    ERR_NOMOTD
           ":MOTD File is missing"
       - サーバの MOTD ファイルを開くことができませんでした．

423    ERR_NOADMININFO
           "<server> :No administrative info available"
       - ADMIN メッセージの応答として，適切な情報の検索に失敗した場合にサーバから返されます．

424    ERR_FILEERROR
           ":File error doing <file op> on <file>"
       - メッセージの処理中にファイル操作の失敗を報告するために使用される一般的なエラーメッセージです．

431    ERR_NONICKNAMEGIVEN
           ":No nickname given"
       - コマンドに期待したニックネームパラメータが見つからなかった場合に返されます．

432    ERR_ERRONEUSNICKNAME
           "<nick> :Erroneus nickname"
       - 定義された文字セットに該当しない文字を含む NICK メッセージを受信した後に返されます．
         有効なニックネームの詳細については，章x.x.xを参照してください．

433    ERR_NICKNAMEINUSE
           "<nick> :Nickname is already in use"
       - NICK メッセージが処理された結果，現在存在するニックネームを変更しようとしたときに返されます．

436    ERR_NICKCOLLISION
           "<nick> :Nickname collision KILL"
       - ニックネームの衝突（他のサーバによってすでに存在するNICKの登録）を検出したときにサーバからクライアントに返されます．

441    ERR_USERNOTINCHANNEL
           "<nick> <channel> :They aren’t on that channel"
       - コマンドのターゲットユーザが指定されたチャネルにいないことを示すために，サーバから返されます．

442    ERR_NOTONCHANNEL
           "<channel> :You’re not on that channel"
       - クライアントがメンバーでないチャネルに影響を与えるコマンドを実行しようとしたときに，サーバから返されます．

443    ERR_USERONCHANNEL
           "<user> <channel> :is already on channel"
       - クライアントが，ユーザが既に参加しているチャネルに招待しようとしたときに返されます．

444    ERR_NOLOGIN
           "<user> :User not logged in"
       - あるユーザに対する SUMMON コマンドがログインしていないために実行できなかった場合に，summon から返されます．

445    ERR_SUMMONDISABLED
           ":SUMMON has been disabled"
       - SUMMON コマンドの応答として返されます．これを実装していないサーバは必ず返さなければなりません．

446    ERR_USERSDISABLED
           ":USERS has been disabled"
       - USERS コマンドの応答として返されます．これを実装していないサーバは必ず返さなければなりません．

451    ERR_NOTREGISTERED
           ":You have not registered"
       - サーバが返す値で，サーバが詳細な解析を許可する前にクライアントを登録する必要があることを示す．

461    ERR_NEEDMOREPARAMS
           "<command> :Not enough parameters"
       - サーバが多数のコマンドで返すもので，クライアントに十分なパラメータが供給されていないことを示す．

462    ERR_ALREADYREGISTRED
           ":You may not reregister"
       - 登録された情報の一部（パスワードや USER メッセージの2番目のユーザ情報など）を変更しようとするリンクに対して，サーバから返されます．

463    ERR_NOPERMFORHOST
           ":Your host isn’t among the privileged"
       - 接続しようとしたホストからの接続を許可するように設定されていないサーバに登録しようとしたクライアントに返されます．

464    ERR_PASSWDMISMATCH
           ":Password incorrect"
       - パスワードが要求された接続の登録に失敗したことを示すために返されるもので，パスワードが与えられなかったか，不正確であったためです．

465    ERR_YOUREBANNEDCREEP
           ":You are banned from this server"
       - 接続を明示的に拒否するように設定されたサーバに接続し，自分自身を登録しようとした後に返されます．

467    ERR_KEYSET
           "<channel> :Channel key already set"

471    ERR_CHANNELISFULL
           "<channel> :Cannot join channel (+l)"

472    ERR_UNKNOWNMODE
           "<char> :is unknown mode char to me"

473    ERR_INVITEONLYCHAN
           "<channel> :Cannot join channel (+i)"

474    ERR_BANNEDFROMCHAN
           "<channel> :Cannot join channel (+b)"

475    ERR_BADCHANNELKEY
           "<channel> :Cannot join channel (+k)"

481    ERR_NOPRIVILEGES
           ":Permission Denied- You’re not an IRC operator"
       - 操作にオペレータ権限が必要なコマンドは，試行に失敗したことを示すためにこのエラーを返さなければなりません．

482    ERR_CHANOPRIVSNEEDED
           "<channel> :You’re not channel operator"
       - chanop 権限を必要とするコマンド（MODEメッセージなど）は，試行するクライアントが指定されたチャネルの chanop でない場合，このエラーを返さなければなりません．

483    ERR_CANTKILLSERVER
           ":You cant kill a server!"
       - サーバ上で KILL コマンドを使用しようとすると，拒否され，このエラーが直接クライアントに返されます．

491    ERR_NOOPERHOST
           ":No O-lines for your host"
       - クライアントが OPER メッセージを送信し，サーバがクライアントのホストからの接続をオペレータとして許可するように設定されていない場合，このエラーを返さなければなりません．

501    ERR_UMODEUNKNOWNFLAG
           ":Unknown MODE flag"
       - ニックネームパラメータを持つ MODE メッセージが送信され，送信されたモードフラグが認識されなかったことを示すためにサーバによって返されます．

502    ERR_USERSDONTMATCH
           ":Cant change mode for other users"
       - 自分以外のユーザのユーザモードを表示または変更しようとしたユーザに送られるエラー．
```

### 6.2 Command responses.
```
300    RPL_NONE
           Dummy reply number. Not used.

302    RPL_USERHOST
           ":[<reply>{<space><reply>}]"
       - USERHOST がクエリリストの返信を一覧表示するために使用する返信フォーマットです．
         返信文字列は以下のように構成されます．
       <reply> ::= <nick>[’*’] ’=’ <’+’|’-’><hostname>
         ’*’ は，クライアントがオペレータとして登録されているかどうかを示す．
         ’-’ または ’+’ は，それぞれクライアントが AWAY メッセージを設定しているか否かを表す．

303    RPL_ISON
           ":[<nick> {<space><nick>}]"
       - ISON が問い合わせリストに対する返信を一覧表示するために使用する返信フォーマット．

301    RPL_AWAY
           "<nick> :<away message>"

305    RPL_UNAWAY
           ":You are no longer marked as being away"

306    RPL_NOWAWAY
           ":You have been marked as being away"
       - これらの応答は，AWAY コマンドと一緒に使用されます（許可されている場合）．
         RPL_AWAY は，離席しているクライアントに PRIVMSG を送信するすべてのクライアントに送信されます．
         RPL_AWAY は，クライアントが接続されているサーバによってのみ送信されます．
         応答 RPL_UNAWAY と RPL_NOWAWAY は，クライアントが AWAY メッセージを削除して設定するときに送信されます．

311    RPL_WHOISUSER
           "<nick> <user> <host> * :<real name>"

312    RPL_WHOISSERVER
           "<nick> <server> :<server info>"

313    RPL_WHOISOPERATOR
           "<nick> :is an IRC operator"

317    RPL_WHOISIDLE
           "<nick> <integer> :seconds idle"

318    RPL_ENDOFWHOIS
           "<nick> :End of /WHOIS list"

319    RPL_WHOISCHANNELS
           "<nick> :{[@|+]<channel><space>}"
       - 返信 311 - 313, 317 - 319 は，すべて WHOIS メッセージに応答して生成される返信です．
         十分な数のパラメータが存在する場合，応答サーバは上記の数値から応答を作成するか（クエリニックが見つかった場合），エラー応答を返す必要があります．
         RPL_WHOISUSER の ’*’ は，ワイルドカードとしてではなく，リテラル文字として存在します．
         各返事セットについて，RPL_WHOISCHANNELS だけが複数回現れるかもしれません(チャネル名の長いリストの場合)．
         チャネル名の横にある ’@’ と ’+’ の文字は，クライアントがチャネルオペレータであるか，モデレートされたチャネルで発言する許可を得ているかどうかを示します．
         RPL_ENDOFWHOIS 応答は，WHOIS メッセージの処理の終了をマークするために使用されます．

314    RPL_WHOWASUSER
           "<nick> <user> <host> * :<real name>"

369    RPL_ENDOFWHOWAS
           "<nick> :End of WHOWAS"
       - WHOWAS メッセージに返信するとき，サーバは提示されたリストの各ニックネームに対してRPL_WHOWASUSER，RPL_WHOISSERVER または ERR_WASNOSUCHNICK の返信を使用しなければなりません．
         すべてのリプライバッチの終わりに，RPL_ENDOFWHOWAS がなければなりません（リプライが1つだけで，それがエラーであったとしても）．

321    RPL_LISTSTART
           "Channel :Users Name"

322    RPL_LIST
           "<channel> <# visible> :<topic>"

323    RPL_LISTEND
           ":End of /LIST"
       - 返信 RPL_LISTSTART，RPL_LIST，RPL_LISTEND は，LIST コマンドに対するサーバの応答の開始，実際のデータによる返信，終了をマークします．
         返送可能なチャネルがない場合，開始と終了のリプライのみを送信する必要があります．

324    RPL_CHANNELMODEIS
           "<channel> <mode> <mode params>"

331    RPL_NOTOPIC
           "<channel> :No topic is set"

332    RPL_TOPIC
           "<channel> :<topic>"
       - チャネルのトピックを決定する TOPIC メッセージを送信する場合，2 つの返信のうち 1 つを送信します．
         トピックが設定されていれば，RPL_TOPIC が返送され，そうでなければ RPL_NOTOPIC が返送されます．

341    RPL_INVITING
           "<channel> <nick>"
       - 試行された INVITE メッセージが成功し，エンドクライアントに渡されることを示すためにサーバから返されます．

342    RPL_SUMMONING
           "<user> :Summoning user to IRC"
       - Returned by a server answering a SUMMON message to indicate that it is summoning that user.
       - SUMMON メッセージに応答したサーバが，そのユーザを呼び出していることを示すために返されます．

351    RPL_VERSION
           "<version>.<debuglevel> <server> :<comments>"
       - サーバがそのバージョンの詳細を示す返信です．
         <version> は使用中のソフトウェアのバージョン（パッチレベルリビジョンを含む），<debuglevel> はサーバが"デバッグモード"で動作しているかどうかを示すために使用されます．
         "コメント欄"には，バージョンに関するコメントや，さらなるバージョンに関する詳細情報を入力することができます．

352    RPL_WHOREPLY
           "<channel> <user> <host> <server> <nick> \
           <H|G>[*][@|+] :<hopcount> <real name>"

315    RPL_ENDOFWHO
           "<name> :End of /WHO list"
       - RPL_WHOREPLY と RPL_ENDOFWHO のペアは，WHO メッセージに答えるために使用されます．
         RPL_WHOREPLY は，WHO クエリに適切なマッチがある場合にのみ送信されます．
         WHO メッセージで供給されるパラメータのリストがある場合，<name> を項目とする各リスト項目を処理した後に RPL_ENDOFWHO を送信する必要があります．

353    RPL_NAMREPLY
           "<channel> :[[@|+]<nick> [[@|+]<nick> [...]]]"

366    RPL_ENDOFNAMES
           "<channel> :End of /NAMES list"
       - NAMES メッセージに返信するために，RPL_NAMREPLY と RPL_ENDOFNAMES からなる返信ペアがサーバからクライアントに返送されます．
         クエリのように見つかったチャネルがない場合，RPL_ENDOFNAMES だけが返されます．
         この例外は，NAMES メッセージがパラメータなしで送信され，すべての可視チャネルとコンテンツが一連の RPL_NAMEREPLY メッセージで送り返され，RPL_ENDOFNAMES で終了をマークする場合です．

364    RPL_LINKS
           "<mask> <server> :<hopcount> <server info>"

365    RPL_ENDOFLINKS
           "<mask> :End of /LINKS list"
       - LINKS メッセージに返信する際，サーバは RPL_LINKS 数値を使用して返信を送り，RPL_ENDOFLINKS 返信を使用してリストの終わりをマークしなければなりません．

367    RPL_BANLIST
           "<channel> <banid>"

368    RPL_ENDOFBANLIST
           "<channel> :End of channel ban list"
       - 特定のチャネルのアクティブな’バン’をリストアップする場合，サーバは RPL_BANLIST と RPL_ENDOFBANLIST メッセージを使用してリストを送り返すことが要求されます．
         アクティブな BANID ごとに個別の RPL_BANLIST が送信されます．
         banids がリストアップされた後（または1つも存在しない場合），RPL_ENDOFBANLIST を送信する必要があります．

371    RPL_INFO
           ":<string>"

374    RPL_ENDOFINFO
           ":End of /INFO list"
       - INFO メッセージに応答するサーバは，そのすべての ’info’ を一連の RPL_INFO メッセージで送信し，返信の終わりを示すために RPL_ENDOFINFO 返信をすることが要求されます．

375    RPL_MOTDSTART
           ":- <server> Message of the day - "

372    RPL_MOTD
           ":- <text>"

376    RPL_ENDOFMOTD
           ":End of /MOTD command"
       - MOTD メッセージに応答し，MOTD ファイルが見つかった場合，RPL_MOTD 形式の返信で，1行80文字以内でファイルを表示します．
         これらは RPL_MOTDSTART（RPL_MOTD の前）と RPL_ENDOFMOTD（後）で囲む必要があります．

381    RPL_YOUREOPER
           ":You are now an IRC operator"
       - RPL_YOUREOPER は，OPER メッセージを正常に発行し，オペレータ・ステータスを得たばかりのクライアントに返送されます．

382    RPL_REHASHING
           "<config file> :Rehashing"
       - REHASH オプションが使用され，オペレータが REHASH メッセージを送信する場合，RPL_REHASHING がオペレータに返送されます．

391    RPL_TIME
           "<server> :<string showing server’s local time>"
       - TIME メッセージに返信する場合，サーバは上記の RPL_TIME 形式を使用して返信を送信する必要があります．
         時刻を示す文字列は，そこに正しい曜日と時刻を含むだけでよいです．
         時刻を示す文字列には，それ以上の要件はありません．

392    RPL_USERSSTART
           ":UserID Terminal Host"

393    RPL_USERS
           ":%-8s %-9s %-8s"

394    RPL_ENDOFUSERS
           ":End of users"

395    RPL_NOUSERS
           ":Nobody logged in"
       - USERS メッセージがサーバによって処理される場合，応答 RPL_USERSTART，RPL_USERS，RPL_ENDOFUSERS，RPL_NOUSERS が使用されます．
         RPL_USERSSTART を最初に送信し，その後に一連の RPL_USERS または単一の RPL_NOUSER のいずれかを送信する必要があります．
         これに続くのは RPL_ENDOFUSERS です．

200    RPL_TRACELINK
           "Link <version & debug level> <destination> <next server>"

201    RPL_TRACECONNECTING
           "Try. <class> <server>"

202    RPL_TRACEHANDSHAKE
           "H.S. <class> <server>"

203    RPL_TRACEUNKNOWN
           "???? <class> [<client IP address in dot form>]"

204    RPL_TRACEOPERATOR
           "Oper <class> <nick>"

205    RPL_TRACEUSER
           "User <class> <nick>"

206    RPL_TRACESERVER
           "Serv <class> <int>S <int>C <server> <nick!user|*!*>@<host|server>"

208    RPL_TRACENEWTYPE
           "<newtype> 0 <client name>"

261    RPL_TRACELOG
           "File <logfile> <debug level>"
       - RPL_TRACE* は，すべて TRACE メッセージに応答してサーバから返されます．
         いくつ返されるかは，TRACE メッセージとそれがオペレータによって送信されたかどうかに依存します．
         どちらが先に発生するか，あらかじめ定義された順序はありません．
         応答 RPL_TRACEUNKNOWN，RPL_TRACECONNECTING，RPL_TRACEHANDSHAKE はすべて，完全に確立されていない接続，不明，まだ接続しようとしている，または’サーバハンドシェイク’の完了プロセスのいずれかに使用されるものです．
         RPL_TRACELINK は，TRACE メッセージを処理し，それを別のサーバに渡す必要があるすべてのサーバによって送信されます．
         IRC ネットワークを横断する TRACE コマンドに応答して送信される RPL_TRACELINK のリストは，そのパスに沿ったサーバ自身の実際の接続性を反映する必要があります．
         RPL_TRACENEWTYPE は，他のカテゴリに当てはまらないが，とにかく表示されている接続に使用されるものです．

211    RPL_STATSLINKINFO
           "<linkname> <sendq> <sent messages> <sent bytes> <received messages> <received bytes> <time open>"

212    RPL_STATSCOMMANDS
           "<command> <count>"

213    RPL_STATSCLINE
           "C <host> * <name> <port> <class>"

214    RPL_STATSNLINE
           "N <host> * <name> <port> <class>"

215    RPL_STATSILINE
           "I <host> * <host> <port> <class>"

216    RPL_STATSKLINE
           "K <host> * <username> <port> <class>"

218    RPL_STATSYLINE
           "Y <class> <ping frequency> <connect frequency> <max sendq>"

219    RPL_ENDOFSTATS
           "<stats letter> :End of /STATS report"

241    RPL_STATSLLINE
           "L <hostmask> * <servername> <maxdepth>"

242    RPL_STATSUPTIME
           ":Server Up %d days %d:%02d:%02d"

243    RPL_STATSOLINE
           "O <hostmask> * <name>"

244    RPL_STATSHLINE
           "H <hostmask> * <servername>"

221    RPL_UMODEIS
           "<user mode string>"
       - クライアント自身のモードに関する問い合わせに答えるために，RPL_UMODEIS が返送されます．

251    RPL_LUSERCLIENT
           ":There are <integer> users and <integer> invisible on <integer> servers"

252    RPL_LUSEROP
           "<integer> :operator(s) online"

253    RPL_LUSERUNKNOWN
           "<integer> :unknown connection(s)"

254    RPL_LUSERCHANNELS
           "<integer> :channels formed"

255    RPL_LUSERME
           ":I have <integer> clients and <integer> servers"
       - LUSERS メッセージの処理では，サーバは RPL_LUSERCLIENT，RPL_LUSEROP，RPL_USERUNKNOWN，RPL_LUSERCHANNELSおよびRPL_LUSERMEから一式の応答を送信します．
         返信するとき，サーバは RPL_LUSERCLIENT と RPL_LUSERME を送り返さなければなりません．
         他の返信は，それらにゼロでないカウントが見つかった場合にのみ送り返されます．

256    RPL_ADMINME
           "<server> :Administrative info"

257    RPL_ADMINLOC1
           ":<admin info>"

258    RPL_ADMINLOC2
           ":<admin info>"

259    RPL_ADMINEMAIL
           ":<admin info>"
       - ADMIN メッセージに返信する場合，サーバは RLP_ADMINME から RPL_ADMINEMAIL までの返信を使用し，それぞれテキストメッセージを提供することが期待されています．
         RPL_ADMINLOC1 には，サーバがある都市，州，国の説明が期待され，次に大学と学科の詳細（RPL_ADMINLOC2），最後に RPL_ADMINEMAIL にサーバの管理連絡先（ここに電子メールアドレスが必要です）が求められます．
```

### 6.3 Reserved numerics.
これらの数値は，以下のいずれかに該当するため，上記では説明しません．

1. もう使用されていない．
2. 将来の使用のために予約されている．
3. 現在使用されているが，現在の IRC サーバの一般的でない’機能’の一部である．

```
209    RPL_TRACECLASS         217    RPL_STATSQLINE
231    RPL_SERVICEINFO        232    RPL_ENDOFSERVICES
233    RPL_SERVICE            234    RPL_SERVLIST
235    RPL_SERVLISTEND
316    RPL_WHOISCHANOP        361    RPL_KILLDONE
362    RPL_CLOSING            363    RPL_CLOSEEND
373    RPL_INFOSTART          384    RPL_MYPORTIS
466    ERR_YOUWILLBEBANNED    476    ERR_BADCHANMASK
492    ERR_NOSERVICEHOST
```

## 7. Client and server authentication
クライアントもサーバも同じレベルの認証が行われます．両者とも，サーバへのすべての接続について，IP 番号とホスト名のルックアップ（およびこの逆チェック）が実行されます．その後，両方の接続に対してパスワードチェックが行われます (その接続にパスワードが設定されている場合)．これらのチェックはすべての接続で可能ですが，パスワードチェックはサーバでのみ一般的に使用されます．

さらに，最近増えているのが，接続に使用したユーザ名のチェックです．接続の相手側のユーザ名を見つけるには，通常，RFC1413 に記載されている IDENT などの認証サーバに接続する必要があります．

パスワードがなければ，ネットワーク接続の相手方を確実に特定することは容易ではないため，サーバ間接続では，ID サーバの使用などの対策に加え，パスワードの使用を強く推奨します．

## 8. Current implementations
このプロトコルの現在の実装は，IRCサーバのバージョン2.8のみです．それ以前のバージョンでは，このドキュメントで説明されているコマンドの一部または全部を，数値応答の多くを NOTICE メッセージに置き換えて実装しているかもしれません．残念ながら，後方互換性の要求のために，この文書のいくつかの部分の実装は，レイアウトされたものと異なっています．顕著な違いとしては

* メッセージ内の任意の LF または CR がそのメッセージの終わりを示すという認識（CR-LFを要求する代わりに）．

この章の残りの部分は，主にサーバを実装しようとする人にとって重要な問題を扱っていますが，いくつかの部分はクライアントにも直接適用されます．

### 8.1 Network protocol: TCP - why it is best used here.
IRC は，TCP がこの規模の会議に適した信頼性の高いネットワークプロトコルを提供しているため，TCP の上に実装されています．マルチキャスト IP の利用も考えられるが，現時点では広く普及し ておらず，サポートされていません．

#### 8.1.1 Support of Unix sockets
Unilx ドメインソケットはリスン/コネクト操作が可能であることから，現在の実装では，Unix ドメインソケット上でクライアントとサーバの両方の接続をリスンして受け入れるように設定することができます．これは，ホスト名が ’/’ で始まるソケットとして認識されます．

Unix ドメインソケットの接続に関する情報を提供する場合，実際のソケット名を要求されない限り，サーバはパス名の代わりに実際のホスト名を指定する必要があります．

### 8.2 Command Parsing
クライアントとサーバに便利な’非バッファード’ネットワークIOを提供するために，各接続には専用の’入力バッファ’が与えられ，最新の読み取りと解析の結果が保持されます．バッファのサイズは512バイトで，1つの完全なメッセージを保持することができます．プライベートバッファは，有効なメッセージの読み取り操作のたびに解析されます．一つのクライアントからの複数のメッセージをバッファで扱う場合，あるメッセージによってクライアントが’削除’されることがないように注意する必要があります．

### 8.3 Message delivery
ネットワークリンクが飽和したり，データ送信先のホストがデータ送信できなくなることはよくあることです．Unix は通常，TCP ウィンドウと内部バッファによってこれを処理しますが， サーバはしばしば大量の送信データを持ち（特に新しいサーバとサーバのリンクが形成されたとき）， カーネルで提供される小さなバッファでは送信キューに十分ではありません．この問題を軽減するために，送信するデータの FIFO キューとして"送信キュー"が使用されます．典型的な"送信キュー"は，新しいサーバが接続するとき，遅いネットワーク接続を持つ大きな IRC ネットワーク上で200Kバイトに成長するかもしれません．

接続をポーリングする際，サーバはまず受信データをすべて読み込んで解析し，送信すべきデータがあればキューに入れます．利用可能なすべての入力が処理されると，キューに入れられたデータが送信されます．これにより，write() システムコールの回数が減り，TCP がより大きなパケットを作成できるようになります．

### 8.4 Connection ’Liveness’
接続が切れたり応答しなくなったりしたことを検知するために，サーバは一定時間内に応答がない接続に対してそれぞれ ping を打つ必要があります．

接続が時間内に応答しない場合，その接続は適切な手順で閉じられます．サーバプロセスがブロックされるよりも遅い接続を閉じる方が良いので，sendq が許容範囲を超えて大きくなった場合にも，接続は切断されます．

### 8.5 Establishing a server to client connection
IRC サーバに接続すると，LUSER コマンドにより，MOTD と現在のユーザ/サーバ数がクライアントに送信されます．また，サーバはクライアントに対して，サーバ名とバージョン，その他適切と思われる紹介メッセージを明確に伝えることが要求されます．

これを処理した後，サーバは新しいユーザのニックネームやその他の情報を自分自身（USER コマンド）で提供したり，サーバが DNS/認証サーバから発見したものを送信する必要があります．サーバは，この情報を NICK の後に USER を付けて送信しなければなりません．

### 8.6 Establishing a server-server connection.
サーバ間の接続は，競合状態をはじめ，さまざまな問題が発生する可能性があるため，危険と隣り合わせのプロセスです．

サーバは，有効であると認識された PASS/SERVER のペアに続く接続を受け取った後，その接続のための自身の PASS/SERVER 情報と，以下に述べるように知っている他のすべての状態情報を返信する必要があります．

開始サーバは PASS/SERVER のペアを受け取ると，応答したサーバが適切に認証されていることを確認した上で，そのサーバへの接続を受け入れます．

#### 8.6.1 Server exchange of state information when connecting
サーバ間で交換される状態情報の順序が重要です．必要な順序は以下の通りです．

* 他のすべての既知のサーバ
* すべての既知のユーザ情報
* すべての既知のチャネル情報

サーバに関する情報は SERVER メッセージ，ユーザ情報は NICK/USER/MODE/JOIN メッセージ，チャネルは MODE メッセージで追加送信されます．

NOT: TOPIC コマンドは古いトピック情報を上書きするため，ここではチャネルトピックは交換されず，せいぜい接続の両側がトピックを交換する程度です．

サーバの状態情報を先に渡すことで，第二サーバが特定のニックネームを導入することによるニックネームの衝突よりも先に，既に存在するサーバとの衝突が発生します．IRC ネットワークは非循環グラフとしてしか存在できないため，ネットワークがすでに別の場所で再接続されている可能性があり，衝突が発生した場所はネットを分割する必要がある場所であることを示しています．

### 8.7 Terminating server-client connections
クライアント接続が終了すると，そのクライアントが接続したサーバがクライアントに代わって QUIT メッセージを生成します．他のメッセージは生成されず，使用されません．

### 8.8 Terminating server-server connections
サーバとサーバの接続が，リモートで生成された SQUIT または’自然な’原因によって閉じられた場合，接続されている残りのIRCネットワークは，閉鎖を検出したサーバによってその情報が更新されなければなりません．サーバは，SQUIT のリスト(その接続の背後にある各サーバについて1つ)とQUITのリスト(再び，その接続の背後にある各クライアントについて1つ)を送信します．

### 8.9 Tracking nickname changes
すべての IRC サーバは最近のニックネームの変更履歴を保持することが要求されます．これは，ニックネームを操作するコマンドでニックネーム変更の競合状態が発生したときに，サーバが状況を把握する機会を持つために必要です．ニックネームの変更を追跡しなければならないコマンドは以下の通りです．

* KILL（キルされるニックネーム）
* MODE（+/- o,v）
* KICK（キックされるニックネーム）

他のコマンドは，ニックネームの変更をチェックさせません．

上記の場合，サーバはまずニックネームの存在を確認し，次にそのニックネームが現在誰に属しているかを確認するために履歴をチェックする必要があります (もし誰かいればですが!)．これは競合状態の可能性を減らしますが，サーバが間違ったクライアントに影響を及ぼしてしまうということはまだ起こり得ます．上記のコマンドで変更履歴を調べるときは，時間範囲を指定し，古すぎるエントリは無視することをお勧めします．

合理的な履歴のために，サーバは，すべてのクライアントが変更することを決めた場合，サーバが知っているすべてのクライアントのために前のニックネームを保持することができるはずです．このサイズは他の要因(例えばメモリなど)によって制限されます．

### 8.10 Flood control of clients
IRC サーバが相互に接続された大規模なネットワークでは，ネットワークに接続している任意の1つのクライアントが連続的にメッセージを供給することは非常に簡単で，その結果，ネットワークが氾濫するだけでなく，他のクライアントに提供するサービスのレベルを低下させることになるのです．大量リクエスト対策は，すべての’犠牲者’に独自の対策を要求するのではなく，サーバに書き込まれ，サービスを除くすべてのクライアントに適用されます．現在のアルゴリズムは以下の通りである．

* クライアントの‘メッセージタイマー‘が現在の時刻より小さいかどうかを確認します（小さい場合は等しくなるように設定します）．
* クライアントから存在するあらゆるデータを読み取ります．
* タイマーが現在時刻より10秒以上進んでいる間に，現在のメッセージを解析し，メッセージごとにクライアントに2秒のペナルティーを課します．

これは要するに，クライアントが2秒に1回メッセージを送信しても悪影響がないことを意味します．

### 8.11 Non-blocking lookups
リアルタイム環境では，すべてのクライアントに公平にサービスを提供するために，サーバプロセスができるだけ待機しないことが重要です．このためには，ネットワーク上のすべての読み取り/書き込み操作において，ノンブロッキング IO が必要であることは明らかです．通常のサーバ接続では，これは難しいことではありませんでしたが，サーバがブロックする可能性がある他のサポート操作（ディスク読み取りなど）があります．可能であれば，そのような動作は短いタイムアウトで実行されるべきです．

#### 8.11.1 Hostname (DNS) lookups
Berkeley などの標準的なリゾルバライブラリを使用すると，返信がタイムアウトになるケースがあり，大きな遅延が発生しました．これを避けるために，DNS ルーチンの別セットが書かれました．これは，ノンブロッキング IO オペレーション用にセットアップされ，メインサーバの IO ループの中からポーリングされます．

#### 8.11.2 Username (Ident) lookups
他のプログラムに組み込んで使用するための ident ライブラリは数多く存在しますが，これらは同期的に動作するため，遅延が頻繁に発生するという問題がありました．この場合も，サーバの他の部分と協調し，ノンブロッキング IO で動作するルーチン群を書くことが解決策となりました．

### 8.12 Configuration File
サーバの設定や運用を柔軟に行うために，以下のようなサーバへの指示を含む設定ファイルを使用することが推奨されます．

* クライアントからの接続を受け付けるホストを指定します．
* サーバとして接続を許可するホストを指定します．
* サーバとして接続を許可するホストを指定します．
* どのホストに接続するか（アクティブおよびパッシブの両方）．
* サーバがどこにあるかという情報（大学，都市／州，会社がその例です）．
* サーバの責任者と連絡可能な電子メールアドレス．
* 制限されたオペレータコマンドへのアクセスを希望するクライアントのホスト名とパスワード．

ホスト名の指定は，ドメイン名とドット表記（127.0.0.1）の両方が可能である必要があります．送信および受信のすべての接続で使用/受信するパスワードを指定できるようにしなければなりません（ただし，送信接続は他のサーバへの接続のみ）．

上記のリストは，他のサーバとの接続を希望するサーバに最低限必要なものです．その他，参考になる項目は以下の通りです．

* 他のサーバが導入できるサーバを指定する．
* サーバの分岐をどこまで深くするか．
* クライアントが接続可能な時間帯

#### 8.12.1 Allowing clients to connect
サーバは，起動時に読み込まれるある種の’アクセス制御リスト’（設定ファイルまたはその他の場所）を使用して，クライアントが接続するために使用するホストを決定する必要があります．

ホストアクセス制御に必要な柔軟性を提供するために，’deny’ と ’allow’ の両方を実装する必要があります．

#### 8.12.2 Operators
破壊的な人物にオペレータの特権を与えることは，その人物に与えられた権限によって，IRC ネット全般の幸福に悲惨な結果をもたらす可能性があります．したがって，そのような権限の取得は非常に簡単であってはなりません．現在の設定では，2つの ’パスワード’ が必要ですが，そのうちの1つは通常簡単に推測されます．オペレーティングシステムのパスワードを設定ファイルに保存することは，ハードコーディングするよりも望ましく，簡単に盗まれないように暗号化されたフォーマットで保存されるべきです (例えば，Unix の crypt(3) を使用します)．

#### 8.12.3 Allowing servers to connect
サーバの相互接続は些細なことではありません．接続不良は IRC の有用性に大きな影響を与える可能性があります．したがって，各サーバは接続できるサーバのリストと，どのサーバがそれに接続できるかのリストを持つべきです．どんな場合でも，サーバは任意のホストがサーバとして接続することを許可してはいけません．どのサーバが接続できて，どのサーバが接続できないかに加えて，設定ファイルにはそのリンクのパスワードや他の特性も保存されるべきです．

#### 8.12.4 Administrivia
ADMIN コマンド（[4.3.7 Admin command](#437-admin-command) 項参照）に対して正確で有効な返答をするために，サーバは設定から関連する詳細を見つけ出す必要があります．

### 8.13 Channel membership
現在のサーバでは，登録したローカルユーザが最大10個の異なるチャネルに参加することができます．非ローカルユーザには制限がないため，サーバはチャネルメンバーシップに関して他のすべてのユーザと（合理的に）一貫性を保つことができます．

## 9. Current problems
このプロトコルにはいくつかの問題があるとされており，近い将来，書き換えの際に解決されることが期待されています．現在，これらの問題に対する実用的な解決策を見つけるための作業が進行中です．

### 9.1 Scalability
このプロトコルは，大規模な舞台で使用する場合，十分にスケールしないことが広く認識されています．主な問題は，すべてのサーバが他のすべてのサーバとユーザについて知っており，それらに関する情報が変更されるとすぐに更新されるという要件から来るものです．また，任意の2点間の経路長が最小に保たれ，スパニングツリーができるだけ強く分岐するように，サーバの数を少なくすることが望まれます．

### 9.2 Labels
現在のIRCプロトコルには，ニックネーム，チャネル名，サーバ名の3種類のラベルがあります．3つのタイプはそれぞれ独自のドメインを持っており，そのドメイン内では重複が許されません． 現状では，ユーザが3種類のラベルのどれかを選ぶことが可能であり，その結果，衝突が発生しています．チャネル名とニックネームが衝突しないような一意な名前にする計画や，サイクリック・ツリーを可能にするソリューションが望ましいと広く認識されています．

#### 9.2.1 Nicknames
IRC におけるニックネームの考え方は，ユーザがチャネル外で会話する際に非常に便利ですが，ニックネームのスペースは有限であり，複数の人が同じニックネームを使いたいと思うことは珍しいことではありません．もしこのプロトコルを使って二人がニックネームを選んだ場合，どちらかが成功しないか，KILL ([4.6.1 Kill message](#461-kill-message)) を使うことで両方が削除されるでしょう．

#### 9.2.2 Channels
現在のチャネルレイアウトでは，すべてのサーバがすべてのチャネル，その住人，プロパティについて知っている必要があります．うまく拡張できないことに加えて，プライバシーの問題も懸念されます．チャネルの衝突は，ニックネームの衝突を解決するために使用されるような排他的なものではなく，新しいチャネルを作成した両方の人々がそのメンバーであるとみなされる包括的なイベントとして扱われます．

#### 9.2.3 Servers
サーバの数は通常，ユーザやチャネルの数に比べて少ないのですが，現在，2つのサーバはそれぞれ個別に，またはマスクの後ろに隠されて，グローバルに知られていることが要求されています．

###  9.3 Algorithms
サーバコード内のいくつかの場所では，クライアントのセットのチャネルリストをチェックするようなN^2アルゴリズムを回避することができませんでした．

現在のサーバのバージョンでは，データベースの整合性チェックがなく，各サーバは隣接するサーバが正しいことを前提にしています．そのため，接続先のサーバがバグっていたり，既存のネットに矛盾を持ち込もうとしたりすると，大きな問題が発生する可能性があります．

現在，内部およびグローバルラベルが一意でないため，多数の競合状態が存在します．これらの競合状態は，一般に，メッセージが IRC ネットワークを横断して影響を及ぼすのに時間がかかるという問題から発生します．一意なラベルに変更することによっても，チャネル関連のコマンドが中断される問題があります．
