# ③python portfolio

## -LINE上で、自動で会話をするchatbot-

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

1.python cgiを使ったスクリプトをFlaskを使ったスクリプトに書き換える

2.ngrokを使いローカル環境で動作確認、及びAIのデータを作成

3.herokuを使いアプリをデプロイ、動作確認。

## 現在の状況

現在の状況から言うと、2工程まで完了しているが、

3工程目のデプロイはまでは完了し、動作確認をしたがうまく動作せず、herokuのlogを確認したところ、



heroku[web.1]: Error R14 (Memory quota exceeded)


heroku[web.1]: Error R15 (Memory quota vastly exceeded)



とあったので、恐らくheroku側のメモリである500Mを超えたためと思われる。

## 結果

・ローカルで正常に動作した

→ ngrokを使用し、URLをLINE Developerに登録し、コマンドで flask　runを実行動作した。↓↓↓下記に動作中の画面有り

・デプロイは完了している

→　gitにpushしURLを取得した

・heroku内部にて、エラーが発生している

という結果が分かった。

## 考えられる改善案

1.herokuに課金し、メモリを上げる

2.コード内のメモリ使用率を確認し、使用率を抑えるコードを書く

## 改善を実行した結果

〇コードのメモリ使用率を確認する

→　コード内のメモリ使用量を確認するために、memory_profileをpipからインストールし、

組み込んでみたが、flaskの高階関数があり、@handler.addからの処理部分ができず、分からなかった

→　herokuのアドオンにソースコードのメモリ使用量や速度を測定するnew relicがというものがあった

で試したがそもそもの heroku add-on 辺りが理解出来ていないのがありうまく組み込めなかった

上記の点での知識が足りていないところがあるため、改善を思案中


## 動作画面(スマフォ画面)
![image](https://github.com/tolafg/chatbot/blob/main/image/Screenshot_20220330_161048_jp.naver.line.android.jpg)
