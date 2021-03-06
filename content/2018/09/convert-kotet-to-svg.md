---
date: 2018-09-08
title: "Kotet SVG化計画"
tags:
- log
- tech
---

前々から自分のアイコンを SVG にしたいと思っていた。
今日、おもむろに Inkscape を起動して絵を書き、生成された SVG を手で非可逆圧縮した。
それが以下の画像だ。

<svg xmlns="http://www.w3.org/2000/svg" style="fill:#000" viewBox="0 0 120 210" width="200">
    <g style="fill:none;stroke:#000;stroke-width:5">
        <path d="m 60,20 c 44,-26 49,-8 49,-8 0,0 9,27 -49,8 z"/>
        <path d="m 60,20 c -51,-14 -54,4 -54,4 0,0 0,27 54,-4 z"/>
        <path d="m 60,20 c -10,49 -1,59 -1,59 8,12 34,44 0,51 -46,9 -43,43 -43,43 0,0 1,32 56,27 55,-5 43,-42 43,-42 0,0 -10,-36 -56,-28"/>
    </g>
    <ellipse cx="40" cy="160" rx="6" ry="9"/>
    <ellipse cx="80" cy="160" rx="6" ry="9"/>
    <g style="fill:#fff">
        <ellipse cx="43" cy="156" rx="2" ry="4"/>
        <ellipse cx="83" cy="156" rx="2" ry="4"/>
    </g>
</svg>

[*Gist*](https://gist.github.com/kotet/8d7824deae79d61dbb4cc29bfb234459)

SVG には様々な利点がある。

### 軽量

普通の画像を SVG に変換したときはどうなのか知らないが、はじめから SVG
で描くととてもファイルサイズが小さくなる。
さらに、JPEG や PNG などと違いプレインテキストのため手で最適化をしやすいという利点もある。
通信インフラが不十分な発展途上国でも Kotet を布教するためには、ファイルサイズが重要である。
今回作った SVG は特に Minify しなくても700バイト以下に収まる。
[いつも使っている PNG 形式のロゴ](/img/common/logo.png)が17キロバイトであることを考えるとこれは驚異的である。

### スケーラブル

Scalable Vector Graphics の名の通り、SVG はスケーラブルである。
拡大してもジャギらない。
さまざまな画面サイズ、画面解像度のデバイスが使われている現在、拡大縮小に耐えうる画像が必要である。
SVG ならちゃんと作ればいくら拡大しても破綻しない。
画素密度の高いディスプレイに対応したウェブサイトを作るとき、
普通なら複数のサイズの画像を用意するか、
一番高密度なディスプレイに合わせてムダにでかい画像を読み込ませなくてはならない。
SVG なら1枚ですべての画素密度に対応し、しかもファイルサイズも圧倒的に小さい。

### 色の変更が簡単

画像の一部分、たとえば自分の場合ロゴの背景色などを変えたいとする。
これがなかなか簡単にはできない。
頑張ればキレイにできるのだろうが、バケツツールで一発とはいかないのだ。
対して SVG ならただのテキストなので、エディタを開いてスタイルを書き換えるだけでいい。
例えば上の画像の色違いも簡単に作れる。

<svg xmlns="http://www.w3.org/2000/svg" style="background-color:#555;fill:#fff" viewBox="0 0 120 210" width="200">
    <g style="fill:none;stroke:#fff;stroke-width:5">
        <path d="m 60,20 c 44,-26 49,-8 49,-8 0,0 9,27 -49,8 z"/>
        <path d="m 60,20 c -51,-14 -54,4 -54,4 0,0 0,27 54,-4 z"/>
        <path d="m 60,20 c -10,49 -1,59 -1,59 8,12 34,44 0,51 -46,9 -43,43 -43,43 0,0 1,32 56,27 55,-5 43,-42 43,-42 0,0 -10,-36 -56,-28"/>
    </g>
    <ellipse cx="40" cy="160" rx="6" ry="9"/>
    <ellipse cx="80" cy="160" rx="6" ry="9"/>
    <g style="fill:#555">
        <ellipse cx="43" cy="156" rx="2" ry="4"/>
        <ellipse cx="83" cy="156" rx="2" ry="4"/>
    </g>
</svg>

### 今後の課題

というわけでロゴを SVG 化したのだが、完成度に少し不満がある。
たとえば曲線がなめらかにつながっていない。
見ているとこれはこれで元絵の雑さが継承されているっぽくて悪くない気もしてくるが、
やはりできないよりはできるようにしておきたい。
ベジェ曲線を自由に使いこなし、自在に線を引けるようになりたい。

今回は Inkscape でマウスを使って描いてから調整したが、理想的には全部エディタで済ませたい。
たぶんそのほうが最適化も簡単かつアグレッシブにできるだろう。

あとは絵心。
絵心が圧倒的に足りない。
SVG でも書いていれば絵心はつくだろうか。
練習としてこれからもロゴの SVG 化の試みを続けていきたい。
