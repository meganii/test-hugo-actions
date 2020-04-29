---
title: "さくらVPSからConoha VPSへのお引越し"
date: 2017-06-11T14:01:22+09:00
lastmod: 2017-06-11T14:01:22+09:00
comments: true
category: ['Tech']
tags: ['VPS','Conoha']
published: true
slug: migration-sakura-vps-to-conoha-vps
img: /images/2017/06/conoha_vps.png
---

{{% img src="/images/2017/06/conoha_vps.png" w="640" h="249" %}}

GMOの株主優待を活かすためにさくらVPSからGMOインターネットのConoha VPSに引っ越しました。これを機に、Dockerでの運用をしたいと考えていたため、合わせてその作業を行いました。

## VPS引越しの動機

昨年、GMOインターネット株式会社の株を購入し、株主優待を受けられるようになりました。GMOインターネットの株主優待では、サービス利用料金のうち年に2回 5,000円のキャッシュバックを受けることができます。株主優待を利用できるサービスには、Conoha VPSやお名前.comなどがありますので、普段VPSやドメイン取得を行っている人にとっては大変ありがたい優待です。

この優待を有効活用するために、VPSを引越しました。また、さくらVPSではCentOS6系で運用していたのですが、昨今のDockerブームに乗っかりDocker化を試みました。

<!--more-->
{{% googleadsense %}}

## 引越しに向けて検討したこと

さくらVPSでやっていたのは、以下の仕事です。

- ブログホスティング(meganii.com)
- 自分用Webサービス
- 自分用APIサービス
- Cronジョブ

まずは以下の通り、可能な限り無料のクラウドサービスを利用することにしました。

| サービス         | 移行先   |
|----------------|----------|
|ブログホスティング | Netlify |
|自分用Webサービス | Heroku  |
|自分用APIサービス | Google Cloud Functions |
|Cronジョブ       | Conoha Rails × Sidekiq|



## 利用金額

１年使った場合の想定です。GMOインターネットのキャッシュバックが激アツです。

|サービス名           |初期費用(円)|月額費用(円)|年費用(円)|キャッシュバック | 実質月額費用(円) |
|-------------------|-----------|----------|---------|--------------|--------------|
|さくらVPS           | 1,620     | 972      | 11,664  | -            | 1,107        |
|さくらVPS(1年契約)   | 1,620     | 891      | 10,692  | -            | 1,026        |
|Conoha VPS         | -         | 972      | 11,664  | -10,000 (*1)  |   139        |


*1: 半年に5,000円が上限


## 感想

３年ほどさくらVPSを利用してきたため、Conoha VPSに移行するのは少し名残惜しいですが、月々の利用料を考えると仕方ないと移行しました。逆に言うと、VPSやドメインを利用している方はGMOインターネットの株主優待を有効活用することで、かなりお得にVPSを利用することができます。

<a href="https://px.a8.net/svt/ejp?a8mat=2TGARC+63OZ02+50+4YR6O2" target="_blank" rel="nofollow">Conoha VPS</a>
<amp-img width="1" height="1" src="https://www11.a8.net/0.gif?a8mat=2TGARC+63OZ02+50+4YR6O2" layout="fixed"></amp-img>


VPSやドメインを利用している方で、GMOインターネットの株主優待に興味がある方はぜひ口座開設してみてください。私は、楽天証券をメインに、GMOクリック証券を利用しています。

- [楽天証券 \| ネット証券（株・FX・投資信託）](https://www.rakuten-sec.co.jp/)
- [GMOクリック証券 \- FXなど投資を身近にもっと便利にするネット証券会社](https://www.click-sec.com/)
