# LINE上で、自動で会話をするchatbot

## APP概要

以前作った、LINE上でオウム返しをするchatbotと、web上で学習し返信をするchatbotを合わせた、

LINE上で学習し会話するchatbot。



## 目的

過去2回botを作成してきたが、今回は2つの特性を合わせたchatbotを作成し、LINEチャンネルを公開する

## 開発環境

windows 11

python 3.9.10

## 動作確認

ngrok

heroku

## ライブラリ

Flask==2.03

line-bot-sdk==2.1.0

後は、pip に予め入っているもの

## 主な工程

1.python cgiのコードにFlaskを導入

2.ngrokを使いローカル環境で動作確認、及びAIのデータを作成

3.herokuを使いアプリをデプロイ、動作確認。

## 現在の状況

現在の状況から言うと、2工程まで完了しているが、

3工程目のデプロイはまでは完了し、動作確認をしたがうまく動作せず、herokuのlogを確認したところ、



2022-04-06T23:58:08.516925+00:00 heroku[web.1]: Error R14 (Memory quota exceeded)


2022-04-07T05:28:11.640836+00:00 heroku[web.1]: Error R15 (Memory quota vastly exceeded)



とあったので、恐らくheroku側のメモリである500Mを超えたためと思われる。

## 考えられる改善案

1.herokuに課金し、メモリを上げる

2.コード内のメモリ使用率を確認し、使用率を抑えるコードを書く

## 改善を実行した結果

〇コードのメモリ使用率を確認する

→　コード内のメモリ使用量を確認するために、memory_profileをpipからインストールし、

組み込んでみたが、flaskの高階関数があり、@handler.addからの処理部分ができず、分からなかった

→　herokuのアドオンにソースコードのメモリ使用量や速度を測定するnew relicがというものがあった

で試したがそもそもの heroku add-on 辺りが理解出来ていないのがありうまく組み込めなかった。

