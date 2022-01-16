# 8.11.1 ホスト名（DNS）ルックアップ

Berkeley などの標準的なリゾルバライブラリを使用すると，返信がタイムアウトになるケースがあり，大きな遅延が発生しました．これを避けるために，DNS ルーチンの別セットが書かれました．これは，ノンブロッキング IO オペレーション用にセットアップされ，メインサーバの IO ループの中からポーリングされます．