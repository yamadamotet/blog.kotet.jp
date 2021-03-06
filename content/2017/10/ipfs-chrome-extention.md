---
date: 2017-10-24
aliases:
- /2017/10/24/ipfs-chrome-extention.html
title: "非中央集権型Web、IPFS体験記4:ブラウザ拡張2"
tags:
- ipfs
- tech
- log
- ipfs体験記
excerpt: 引き続き公式ブラウザ拡張の機能を見ていく。
---

引き続き公式ブラウザ拡張の機能を見ていく。

### WebUIを開く

シンプルながら地味に便利。

### 接続ノード数表示

異常が起きてたらすぐわかるかもしれない。

### リソースのpin/unpin

ネットワーク上で誰もリソースを持っている人がいないと、そのリソースにはアクセスできなくなる。
IPFSリソースにアクセスすると一時的にそれがローカルに保存され(、おそらくそのリソースの配信者にな)るが、GCの動作時に削除される。
リソースをpinするとリソースをずっと消さずにとっておくことができる。

現状他人のリソースをpinするインセンティブがないので、基本的にリソースの配信者はリソースを追加した人自身か、
公式パブリックゲートウェイか、ボランティア精神でなんでもpinしている人か、
偶然ビットレベルで全く同じリソースを追加した人のみである。
とりあえず自分がアクセスしたものは全部Pinしておこうと思う。
インセンティブづくりについてはFilecoinなどが関係しているようだが、まだよくわからない。

### Quick Upload

`ipfs add`のGUI版。
やっぱり簡素でもGUIがあるととっつきやすさが違うと思う。
ディレクトリには対応していないようだ。

### IPFSプロトコルのサポート

これは設定画面ではExperimentalの項目にあるが、デフォルトで有効になっている。
`ipfs://`や`ipns://`、`dweb:/ipfs/`という形式のリンクやリクエストをサポートするらしい。
この形式を使っている人は少ないし、
このExtentionを入れた人でないとアクセスできないので利用機会は少ないかもしれない。

### IPFSアドレスのリンク化

こちらもExperimental。
デフォルトで無効。
`/ipfs/`形式の文字列をリンクに置き換える。
コマンドなどから得たアドレスをそのままコピペできるのか！？
と思ったがアドレスバーにコピペしても何も起きなかった。
大抵の場合ipfsアドレスは最初からゲートウェイへのリンクにする配慮がされているので、使うときはすくないかもしれない。

以上でだいたいの機能は挙げられたと思う。
次回は実際にいろいろ試そうと思う。
