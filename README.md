# Google Cardboard VR MVP

## 概要

Google Cardboard向けに作成した、HTMLファイル1枚で動作するVRコンテンツのMVP（Minimum Viable Product）です。

ゲームを作ることが目的ではなく、今後VRゲームへ発展させるための土台を構築することを目的としています。

主な検証項目は以下です。

* Google Cardboardで360°空間を見回せること
* 視線（Gaze）によるインタラクション
* シンプルなVR UI
* スマートフォンブラウザで動作すること

👉 **[テスト画面を開く](https://nanashiai.github.io/vr-test/)**

---

# 現在の実装内容

## VR空間

* 360°空間
* 6面を色分けした部屋
* Three.jsによる描画

色分け

* 前：赤
* 後：青
* 左：緑
* 右：黄
* 天井：白
* 床：灰色

---

## 視線カーソル

画面中央にレティクル（照準）を表示します。

---

## Gazeインタラクション

立方体を約2秒見続けると

* 色がランダムに変化
* 「Hello VR」を表示

視線を外すと

* ポップアップを閉じる
* Gazeタイマーをリセット

---

## Cardboardモード

画面を左右2画面へ分割する簡易Cardboardモードを搭載しています。

※本実装は簡易的な二眼表示であり、WebXRやGoogle Cardboard SDK相当のレンズ補正は行っていません。

---

## デバッグ機能

画面左上へ以下をリアルタイム表示します。

* HTTPS状態
* センサーイベント数
* 使用中イベント
* hasGyro
* alpha
* beta
* gamma
* Screen Orientation
* Camera Quaternion
* Frame数

ジャイロが動作しない場合の原因調査用です。

---

# 動作環境

推奨

* Android
* Google Chrome
* Google Cardboard

ライブラリ

* Three.js r128（CDN利用）

---

# HTTPSについて

Chromeでは、Device Orientation APIはセキュアコンテキストでの実行が推奨・要求されます。

以下の環境で利用してください。

* https://
* localhost
* 127.0.0.1

`file://` や通常のHTTPでは、端末やブラウザの仕様によってセンサーが利用できない場合があります。コード内にもHTTPS状態を確認する処理を実装しています。

---

# 開発目的

このプロジェクトは「完成品」を目指すものではありません。

HTMLファイル1枚という制約の中で、

* VR表示
* Gaze操作
* ジャイロ制御
* UI

などの基礎技術を検証し、今後のVRゲーム開発の土台として育てていくことを目的としています。
