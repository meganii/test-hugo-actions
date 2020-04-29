---
title: "[デブサミ2018夏]機械学習チームにおけるソフトウェアエンジニア〜役割、キャリア"
date: 2018-07-27T13:03:22+09:00
lastmod: 2018-07-27T13:03:22+09:00
comments: true
category: ['Tech']
tags: ['データ分析基盤']
published: false
slug: developers-summit-2018-summer-cookpad
img: https://res.cloudinary.com/meganii/image/upload/c_thumb,w_200,g_face/v1532741609/developers-summit-2018-summer_pcc1uq.png
---

<!--more-->
{{% googleadsense %}}

## Profile

- takahi_i

データ分析ガチ勢は、博士

## Topic

- 機械学習チームにおけるソフトウェアエンジニアの役割


## 機械学習プロジェクト

- コードだけで完結しない
- モデルないに振るマイが隠蔽される
- 入力データ
- 知見共有して安全性を確保するのが難しい
    - 特にアルゴリズム自体が難しい場合

最近の流れ
- 機械学習の導入、管理の難しさをエンジニアリングで対処
- ソフトウェアエンジニアはどういった貢献をするべき？


ライフサイクル
1. 実験
    - Jupyter Notebookを利用して探索的な試行錯誤
2. コード整理
    - ライブラリか、リファクタリング
3. デプロイ
    - サービスか、CD、監視

- 上記サイクルを回転させていく

悪いプロジェクトの場合
- サイクルが回らない、回しにくい => モデルが固定
- 精度が上がらない
- デプロイコストが大きい


求められること
- プロジェクトのサイルクルを高速、安全に回せる環境の整備
    - 3つのステージの問題をエンジアリングで解決していく




実験ステージ
- データの取得
- 計算機リソース

データ取得する環境を構築する前に、

- データサイエンティストのアウトプットは、データ取得コストに依存する

データにアクセスできないデータサイエンティストとは？　=>　丘サーファー


1. データベースのテーブル群
2. ログ

データサイエンティストが自分でアクセスできる環境が必要


データ分析基盤
- 自社　Hive, Spark, Presto
- ホスティング　BigQuery, Redshift, TreasureData

社内のあらゆるデータを分析基盤に載せる

ログ収集ツールを利用して自動でデータを投入する仕組みを整える
- logstash, fluentd, embulk



Cookpad 事例紹介

- DQHチームが担当 (Redshiftをベース)
- 必要なデータはSQLで取得できる


2. 計算機リソース

- 複数人で単一サーバにログインして作業
- リソースが足りなくて実験が進まない
- GPUが足りない x 

- [cookpad]slackで計算機リソース管理でEC2インフラ管理している

コード整理ステージ
1. コードが理解できない
2. ポータビリティが無い

実験スクリプトが理解できない
- なんか動作しているようだが、モデルを生成しているコードがりかいできない
    - Jupyter Notebookをそのままコピペ
- まずは、NotebookをちゃんとしたPython scriptに落とし混む

スクリプト化
- 実験フローの構造化（べた書きから関数化、クラスの抽出）
- 頑健性の確保（リファクタリング、テスト）



自動テスト
- 最低限、前処理、End-toEndoのテストは書く
- c.f. 初めての自動テスト


テストの恩恵
- テスト = 仕様
- CIで動作するテストには齟齬がない
- 引き継ぎ時に、かなり助かる


- 継続的インテグレーション入門


[アンチパターン]リサーチャが検証した実験内容を園児あが整理してデプロイ
- 次に修正するときに、リサーチャは自分のコードじゃない、プログラマはアルゴリズムは知らない
- [cookpad]コード整理時に、リサーチャとエンジニアのペアを作る
- コードの知見を共有しつつ作業
- チームのメンバのコーディング能力を均一化

ポータビリティがない
- スクリプトを実行する環境が作れない
- 機械学習を扱うスクリプトは多数のライブラりに異存
- python以外の言語で記述されたツールにも異存（mecab）
    - ローカルで動いているけど、デプロイ先のlinuxでは動かない

- [cookpad]dockerを導入
- Pythonライブラリ以外


理想
- 実験段階からDockerで作業
- ステージが変わっても確実にスクリプトが動作する環境が手に入る
- 結果、サイクルを回しやすい

[cookpad] Cookiecutter Docker Science
- Docker環境での実験〜デプロイまでをサポートするテンプテートを作る
- docker commandをmakeで隠蔽
- ファイル、ディレクトリ構成を統一（誰もが同じディレクトリ構成になる）
    - data, model, 

デプロイステージ
- サーバ構築やバッチスクリプトで機械学習の結果をでプリ
- 生産性は組織のインフラ技術に依存する


cookpad
- 機械学習チーム自身でプロダクション環境に
- 機械学習プロジェクトの設定共通化


- @_lunardog_ Kelner


まとめ
- ケアする部分がたくさん
- 厳密に分業体制を気づくのは難しいため、各自の能力のoverlap 部分を増やすのが重要（レビュー、ペアプロで知見共有）


## Web企業におけるキャリア形成

- 同じMLチームでもチーム規模によってキャリアが異なる



小さなMLチームメンバ
- マルチスタック化
- 一人で

大きなMLチーム
- 専門に特化した経験を積める
    - リサーチャ
    - インフラ


## Git
- Rebase, stash, squash, bisect
- Docker
- テスト自動化
- Jira, Rdmine


- 8名: 中ぐらいの規模
- 機械学習園児あ
- インフラ園児あ

分析基盤、全社インフラチーム



## キャリア形成

- サービスをよりよくする技術
    - 会社が期待するニーズと違う成果を出すと解散
- ML/AL需要が元帥しても
    - マルチスタック化 / １点突破

## 生存戦略１
- 関技技術も習得してマルチスタック化
    - 検索エンジン チョットデキル
- 機械学習以外にも会社に貢献する

- ストレージ
    - 検索エンジン（）
    - データベース
- インフラ技術
    - ワークフロー Airflow
    - 構成管理 
    - サーバー管理
- 分析基盤
    - 初歩：SQL
    - 中級：ビックデータフレームワーク
    - 利用: 分析基盤の改善にも貢献

## 生存戦略2

- 分野としての
- 中途半端な理解、アウトプットで生き残るのは難しい
  (数学、物理学分野の終始、博士から転身が進んでいる)