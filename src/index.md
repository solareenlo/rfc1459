```
Updated by: 2810, 2811, 2812, 2813, 7194                    Experimental
                                                            Errata exist
Network Working Group                                      J. Oikarinen
Request for Comments: 1459                                      D. Reed
                                                               May 1993
```

<h1 align="center">
Internet Relay Chat Protocol
</h1>

## IRC

- [RFC 1459](https://solareenlo.com/rfc1459) (Internet Relay Chat Protocol)
- [RFC 2810](https://solareenlo.com/rfc2810) (Internet Relay Chat: Architecture)
- [RFC 2811](https://solareenlo.com/rfc2811) (Internet Relay Chat: Channel Management)
- [RFC 2812](https://solareenlo.com/rfc2812) (Internet Relay Chat: Client Protocol)
- [RFC 2813](https://solareenlo.com/rfc2813) (Internet Relay Chat: Server Protocol)
- [RFC 7194](https://solareenlo.com/rfc7194) (Default Port for Internet Relay Chat (IRC) via TLS/SSL)

## 本メモの位置付け

このメモでは、インターネットコミュニティのための実験的なプロトコルを定義しています。改善のための議論と提案が望まれます。このプロトコルの標準化状態やステータスについては、"IAB Official Protocol Standards" の最新版を参照してください。このメモの配布は無制限です。

## 概要

IRC プロトコルは、BBS でユーザー同士がチャットする手段として実装されて以来、4年の歳月をかけて開発されたものです。現在では、サーバとクライアントの世界的なネットワークをサポートし、成長に対応するためにひもじい思いをしています。過去2年間で、IRC の主要ネットワークに接続しているユーザーの平均人数は10倍に増加しています。

IRC プロトコルはテキストベースのプロトコルであり、最も単純なクライアントはサーバに接続可能な任意のソケットプログラムです。
