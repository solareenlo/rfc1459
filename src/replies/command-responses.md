# 6.2 Command 応答

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
