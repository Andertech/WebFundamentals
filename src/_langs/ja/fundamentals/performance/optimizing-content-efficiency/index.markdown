---
layout: section
title: "コンテンツの効率性の最適化"
description: "アプリでダウンロードされるデータの量は増え続けています。パフォーマンスを最適にするには、バイト 1 つ 1 つの配信を最適化する必要があります。"
introduction: "ウェブ アプリケーションは、その対象範囲、規模、機能の点で成長を続けています。それは良いことですが、ウェブを充実させるための絶え間ない進歩は、アプリケーションでダウンロードされるデータの量も一定のペースで増え続ける、という傾向も招いています。パフォーマンスを最適にするには、バイト 1 つ 1 つの配信を最適化することが必要です。"
article:
  written_on: 2014-04-01
  updated_on: 2014-04-29
  order: 2
id: optimizing-content-efficiency
authors:
  - ilyagrigorik
collection: performance
---

{% wrap content%}

<style>
  img, video, object {
    max-width: 100%;
  }

  img.center {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
</style>

最近のウェブ アプリケーションはどうなっているのでしょうか。この答えは [HTTP Archive](http://httparchive.org/) で見つかります。このプロジェクトでは、人気の高いサイト（Alexa の上位 100 万件のサイトリストのうち 300,000 件以上）をクロールし、各サイトのリソースの数、コンテンツの種類、その他のメタデータに関する分析を記録し集約することで、ウェブがどのように構築されているかを追跡しています。

<img src="images/http-archive-trends.png" class="center" alt="HTTP Archive の傾向">

<table class="table-4">
<colgroup><col span="1"><col span="1"><col span="1"><col span="1"></colgroup>
<thead>
  <tr>
    <th></th>
    <th>50 パーセンタイル</th>
    <th>75 パーセンタイル</th>
    <th>90 パーセンタイル</th>
  </tr>
</thead>
<tr>
  <td data-th="種類">HTML</td>
  <td data-th="50%">13 KB</td>
  <td data-th="75%">26 KB</td>
  <td data-th="90%">54 KB</td>
</tr>
<tr>
  <td data-th="種類">画像</td>
  <td data-th="50%">528 KB</td>
  <td data-th="75%">1213 KB</td>
  <td data-th="90%">2384 KB</td>
</tr>
<tr>
  <td data-th="種類">JavaScript</td>
  <td data-th="50%">207 KB</td>
  <td data-th="75%">385 KB</td>
  <td data-th="90%">587 KB</td>
</tr>
<tr>
  <td data-th="種類">CSS</td>
  <td data-th="50%">24 KB</td>
  <td data-th="75%">53 KB</td>
  <td data-th="90%">108 KB</td>
</tr>
<tr>
  <td data-th="種類">その他</td>
  <td data-th="50%">282 KB</td>
  <td data-th="75%">308 KB</td>
  <td data-th="90%">353 KB</td>
</tr>
<tr>
  <td data-th="種類"><strong>合計</strong></td>
  <td data-th="50%"><strong>1054 KB</strong></td>
  <td data-th="75%"><strong>1985 KB</strong></td>
  <td data-th="90%"><strong>3486 KB</strong></td>
</tr>
</table>

上記のデータから、2013 年 1 月～2014 年 1 月の間、一般的なウェブサイトでダウンロードされたデータの容量は増加傾向にあったことがわかります。もちろん、必ずしもすべてのサイトが同じ割合で成長しているわけでも、同じデータ容量を必要としているわけでもありません。ここでは分布内のさまざまな分位点（50 番目（中央値）、75 番目、90 番目）に焦点を当てています。

中央値のサイトは 2014 年初めには 75 のリクエストで構成され、転送されたバイト数を合計すると 1054 KB になり、合計バイト数（とリクエスト数）は、前年を通して一定のペースで増加し続けています。これ自身はそれほど驚く数字ではありませんが、これはパフォーマンスに重大な影響をもたらします。おわかりのように、インターネットは高速化しているものの、国によって高速化の程度は異なり、特にモバイルでは、いまだに多くのユーザーにデータ容量の上限と高額の従量性プランが課せされています。

デスクトップ アプリケーションと異なり、ウェブ アプリケーションはインストールを別個に行う必要がありません。URL を入力すれば終わりです。それがウェブの主となる特徴です。しかし、このためには、**数十、場合によっては数百という各種リソースを取得する必要があり、それをすべて加算するとデータ容量は数メガバイトになる可能性があります。また、目的とするウェブ エクスペリエンスを瞬時に提供するには数百ミリ秒単位でまとめて受信することも必要です。**

これらの要件を踏まえてウェブ エクスペリエンスを瞬時に実現することはやさしいことではありません。だから、コンテンツの効率性を最適化することは重要なのです。不要なダウンロードを取り除き、さまざまな圧縮技術で各リソースの転送エンコードを最適化し、冗長なダウンロードを取り除くことが可能な場合は常にキャッシュを利用することです。

{% endwrap %}

