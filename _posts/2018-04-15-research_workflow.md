---
layout: post
title: 研究ワークフロー
date: 2018-04-15
tags: research
---

研究を行うにあたってサーベイから実装，実験，論文執筆までの効率的なワークフローを確立することは非常に重要です．
このポストは自身の研究ワークフローを紹介し，誰かのためになればいいですという大義名分とともに，もっといい方法があれば教えてほしいという下心もあります．  
一番下に2018年4月に名古屋CV・PRML勉強会で発表したときの資料もあります．  
私のワークフローはDustin Tran氏のワークフローを参考にしています．[<sup>1</sup>](#脚注)

## 論文管理

![](/images/post-images/2018-04-08-figure1.png)

論文管理には[Papers](https://www.readcube.com/)を使っています．（PapersはReadCubeに統合される予定らしい）
自分の好きな粒度で分野ごとにディレクトリを作成して，論文を管理しています（`Field/Paper`）．
ただし，自分の研究に関連する分野は`Research/Field/Paper`としています．
基本的にiPad+Apple pencilで論文に手書きメモを加えながら読んでいます．
一応，論文管理アプリの代表であるMendeleyと比較したPapersの利点と欠点を下に書いておきます．[<sup>2</sup>](#脚注)

## プロジェクト管理

研究プロジェクトの管理にはGitHubを使っています．
１つのプロジェクトは１つのリポジトリで管理します．
リポジトリ内のディレクトリ構成は以下の通りです．

```
-- doc/
 -- YYYY-conferencename/
  -- fig/
  -- main.pdf
  -- main.tex
-- etc/
 -- YYYY-MM-DD-whiteboard.jpg
 -- YYYY-MM-DD-enomoto-comments.md
-- src/
 -- checkpoints/
  -- YYYYMMDD_%H%M%S_hyperparameters/model
 -- codebase/
 -- log/
  -- YYYYMMDD_%H%M%S_hyperparameters/log
 -- out/
  -- YYYYMMDD_%H%M%S_hyperparameters/output
 -- script1.py
 -- script2.py
-- .editerConfig
-- .gitignore
-- README.md
```

`README.md`にはプロジェクトに関するTODOリストを書いておきます．

`doc/`には論文執筆に必要なファイルを全て入れておきます．

`etc/`には`doc/`や`src/`には入らないファイルを全て入れておきます．
Dustin Tran氏はディスカッション時のホワイトボードの写真や，日々出てきたアイデアを書いてあるファイルをおいておくそうです．

`src/`には全てのコードを入れておきます．
`src/`直下には直接実行可能なコードのみをおいておき，その他のコードは`codebase/`以下に入れておきます．
`checkpoints/`には学習済みモデル，`log/`には学習のログ，`out/`にはローカル環境で確認したい結果を全て入れておきます．
`checkpoints/`や`out/`はサイズが大きくなることが予想されるので`.gitignore`に記述しておきます．
`.editerConfig`を設定しておくと編集環境による差異を吸収できます．

大規模データはサーバ上の特定のディレクトリにまとめておきます．

## 実験

以下では，遠隔のサーバ上でプログラムを走らせることを前提としています．

まず，コードはローカル環境で編集します．
サーバで実行する段階になったら，`rsync`コマンドでGit管理していないファイルも含めて全てサーバに送ります(サーバとローカルで`.git/`を共有しないとGit管理がめちゃくちゃになります）．
サーバ・ローカル間のファイル共有でターミナルを頻繁に使うので，エディタは統合ターミナルがあるものがおすすめです（私はVisual Studio Codeを使っています）．
コードをサーバに送ったら，サーバに接続し`tmux`上でプログラムを走らせます．[<sup>3</sup>](#脚注)

ハイパーパラメータが存在する場合は極力プログラム実行時にオプションで指定できるようにしておきます．
Pythonの`argparse`モジュールが便利です．
ハイパーパラメータとしてバッチサイズと学習率が存在し，
```
python script1.py --batch_size=256 --lr=1e-4
```
というコマンドを実行した場合，`checkpoints/`, `log/`, `out/`のサブディレクトリは`YYYYMMDD_%H%M%S_batch_size_256_lr_1e-4/`とします．

出力データ，特に画像などの直接サーバ上で確認できないデータは全て`out/`に出力し，`rsync`コマンドでローカルと共有します．

実験の観察・考察には[Comet.ml](https://www.comet.ml/)を使います．[<sup>4</sup>](#脚注)
GitHubのリポジトリごとにComet.mlでもプロジェクトを作成します．
複数の実験を同一ウィンドウで比較できたりするので非常に便利です．
オプション指定した値を自動で記録してくれるため，ハイパーパラメータの管理も簡単です．

## 論文執筆
To be added

## まとめ

1. Papersで論文管理&サーベイ
1. ローカルでコード編集（Visual Studio Code）
1. `rsync`でコードをサーバと共有（Visual Studio Codeの統合ターミナル）
1. サーバの`tmux`上でプログラムを走らせる
1. `rsync`で出力データをローカルと共有（Visual Studio Codeの統合ターミナル）
1. Comet.mlで考察

## 脚注

<sup>1</sup> [A Research to Engineering Workflow](http://dustintran.com/blog/a-research-to-engineering-workflow)

<sup>2</sup> Mendeleyと比較したPapersの利点と欠点

### 利点

* 論文への手書きメモが可能．論文読みはiPad+Apple pencilが最高．MendeleyからPapersに乗り換えた理由はほぼこれ．
* 2層以上の管理ディレクトリが作成可能．Mendeleyでも分野ごとにディレクトリを作成していましたが自分の研究に関係する分野は`Research/Field/Paper`としたい．
* アプリ内から論文を検索，インポート可能．google scholar, arXiv, IEEE Exploreなど．MendeleyではiPadやiPhoneでの論文追加は難しかったが，この機能により簡単になった．アプリ内で論文をインポートすれば文献情報も全て追加される．
* bibtex生成可能．ただし，文献情報が付随していれば．
* UIが使いやすい．スマホ，タブレットアプリは特に使いやすい．

### 欠点

* D&DでPDFをPapersに追加しても文献情報が追加されない．
* 有料．

<sup>3</sup> [おすすめtmux設定](https://github.com/gpakosz/.tmux)

<sup>4</sup> Comet.mlの導入コストは非常に少ないです．まだローンチされたばかりのサービスらしくバグも多いですが，個人的に期待しているサービスの１つです．

<iframe src="//www.slideshare.net/slideshow/embed_code/key/f0lScHZOFQ3zAY" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/enoken/cvprml-20180421" title="研究ワークフロー@名古屋CV・PRML勉強会 2018-04-21" target="_blank">研究ワークフロー@名古屋CV・PRML勉強会 2018-04-21</a> </strong> from <strong><a href="https://www.slideshare.net/enoken" target="_blank">enoken</a></strong> </div>