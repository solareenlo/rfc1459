# 3.3 1対全

1対全のメッセージはブロードキャストメッセージと呼ばれ，すべてのクライアントまたはサーバ，あるいはその両方に送信されます．ユーザとサーバからなる大規模なネットワークでは，1つのメッセージによって，希望するすべての宛先に到達するために，ネットワーク上で多くのトラフィックが送信されることになります．

メッセージによっては，各サーバが持つ状態情報がサーバ間で適度に整合するように，全サーバにブロードキャストする以外の選択肢はありません．
