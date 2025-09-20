## 今日やったこと
1. Javaコンソールアプリ開発:1.75h  

## 学び  
1. StreamAPIを使った条件絞り込み実装
   - filterメソッドを使うことで条件の絞り込みができる

2. 標準API&GradleのDB接続処理について
   - src/main/resources配下にファイルを配置するのが基本
     - app.propertis:DB設定
     - SQLファイルの配置(schema.sql,data.sqlなど)
   - try-with-resources構文を使って確実にリソースをcloseする設計が重要
   - 接続情報の初期化クラス(DbInitializerクラス)を定義し、Mainクラスで呼ぶ構成にする。

## 所感
1. DB関連のファイルはsrc/main/resourcesに配置することを学べた。
2. プログラム実行が手動実行で手間なのでWindowsバッチを使って自動化したい。
3. インメモリからDBに切り替える際にクラス差し替えを行うのでDIの利便性を確かめたい。
---

## 今後のTodo
1. h2DBの接続設定&疎通確認
2. delete,updateなどの処理を実装