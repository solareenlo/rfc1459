# 2.3 メッセージ

サーバとクライアントは互いにメッセージを送り合い，返信が発生することもあればしないこともあります．メッセージに有効なコマンドが含まれている場合，後の章で説明するように，クライアントは指定されたとおりの返信を期待すべきですが，返信を永遠に待つことはお勧めできません．クライアントからサーバ，サーバからサーバへの通信は，本質的に非同期的な性質を持っています．

各 IRC メッセージは，プレフィックス（オプション），コマンド，コマンド・パラメータ（最大15個まで）の3つの主要部分から構成されます．プレフィックス，コマンド，およびすべてのパラメータは，1つ（または複数）の ASCII スペース文字（`0x20`）で区切られます．

プリフィックスの存在は，先頭の ASCII コロン文字（`:`，`0x3b`）1つで示され，これはメッセージ自体の最初の文字でなければなりません．コロンとプレフィックスの間に隙間（ホワイトスペース）があってはいけません．プレフィックスは，サーバがメッセージの本当の出所を示すために使われます．メッセージにプレフィックスがない場合，そのメッセージは受信した接続から発信されたものとみなされます．クライアントは自分自身からメッセージを送るときには prefix を使うべきではありません． もし prefix を使うなら，有効な prefix はそのクライアントに関連付けられた登録済みの ニックネームだけです．プレフィックスによって識別される送信元がサーバの内部データベースから見つからない場合，あるいは送信元がメッセージの到着元とは異なるリンクから登録されている場合，サーバはそのメッセージを黙って無視しなければなりません．

コマンドは，有効な IRC コマンドか，ASCII テキストで表現された(3)桁の数字でなければなりません．

IRC メッセージは常に CR-LF（Carriage Return - Line Feed）ペアで終了する文字列であり，メッセージの長さは最後の `CR-LF` を含むすべての文字を含めて512文字以下でなければなりません．したがって，コマンドとそのパラメータに許容される文字数は最大510文字です．継続メッセージ行の規定はありません．現在の実装の詳細については，章[7. クライアントとサーバーの認証](../client-and-server-authentication/index.md)を参照してください．