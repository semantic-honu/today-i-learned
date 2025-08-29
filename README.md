# today-i-learned
A collection of things I learned today.  
今日学んだことの記録を書いていきます。


## 2025年
### 8月28日
- picoCTF
  - zsteg を使ってみました。できることは以下。
   1. LSB (Least Significant Bit) 解析
   2. ファイルヘッダーの検出
   3. ​隠されたテキストの抽出
  - `echo "見つかったbase64文字列" | base64 -d`でbase64デコードができる。
  - ​.pcapファイルはパケットキャプチャファイルをwiresharkとtsharkで解析。tcpペイロードを取り出す。
  - sha256sumでハッシュ値を生成する。
  - zbar-toolsでQRコードを解析する。
- Windowsのシステム整合性修復の方法を学びました。  
```
ログチェック:イベントビューア
診断：DISM /Online /Cleanup-image /ScanHealth
​修復：DISM /Online /Cleanup-image /RestoreHealth
​システムファイルの整合性チェック：sfc /scannow
```
- wingetのアップデート問題：メジャーバージョンアップグレードの特性を理解して手動で対応
- ログイン前のキーボード設定の修正方法を学びました。  
`sudo vim /etc/default/keyboard``sudo dpkg-reconfigure keyboard-configuration
`
- サイバーセキュリティ
  - 侵入方法とRaaSの分業体制を学びました。  
攻撃者は侵入と権限昇格までを行い、RaaSとは分業である。RaaSはLiving off the Land、certutilやbitsadmin、MWIなど標準ツールの悪用が主流となっている。



### 8月27日
- Git＆GitHub
  - Gitのコマンドについて学習しました。`git add .`の危険性を理解し、`git add <file>`の重要性を学びました。  
→コミットは意味のある単位で行うことが重要。
  - GitHubの`TIL`（Today I Learned）というプラクティスについて調べ、実践しました。  
→アウトプットと手軽さの重要性。
  - web上でgit操作する方法を調べ、実践しました。

- DBのmaster/slave構成性について学びました。  
→データを複製して冗長性や読み込みパフォーマンスを向上させる仕組み。レプリケーションにより別DBにバイナリログを転送、slaveに適用する。

- Linux Ubuntu
  - `apt autoremove`は必要のなくなった依存関係のパッケージを自動的に判断して削除してくれるコマンド。
  - 日本語入力環境ではFcitx5の設定で、入力メソッドを、第一入力に**「キーボード - 日本語」、第二入力に「Mozc」**という組み合わせがスムーズに動く。
  - `sudo apt install gnome-shell-extension-manager`経由でInput Method Panelをインストール。  
→検索ボックスの表示位置を整える。

```
GNOME Shell とその他の関係
​OS（Ubuntu）：コンピューター全体の土台。
​Wayland/X11：アプリケーションとデスクトップ環境の間で、グラフィック描画などの通信を行うためのプロトコル。
​GNOME Shell：WaylandやX11と連携して、UIの見た目や操作を管理する。
​Fcitx5：GNOME Shell上で動作する日本語入力システム
```

- picoCTF
  - .dd.gzのディスクイメージのフォレンジック問題を解きました。  
→まずgzipで解凍。その後、stringsとgrepをパイプラインで繋げて使用したり、`strings file.dd > strings_output.txt`でテキストに書き出したり。マウントしたり。

- BLE、またMQTTとCoAP通信の違いについて学びました。  
→BLEは低レイヤープロトコル。MQTTとCoAPはアプリケーション層のプロトコル。
  - MQTT:TCP、非同期、Pub/Sub
  - CoAP:UDP、即時、サーバークライアント型

- Python:Kaggle
  - docstringとjavadocの違いを学びました。  
→javadocは実行時に無視されるコメントだが、docstringは実行時に存在する。基本は複数行文字列だが、何処にも代入していない場合は、コメントのように扱える。
  - True,Falseの扱いがJavaと違うことを学びました。  
→意味のある値が入ってればTrue、空の値ならFalse。0,1が使えるから真偽判定と計算が同時に行える。
  - `not A and not B`は`not (A or B)`に因数分解できる。ドモルガンの法則。
  - returnに条件式を書くのが簡潔な書き方。
  - nullはなく、None。
  - `if not <list>`でnullと空チェックが同時に出来る。
