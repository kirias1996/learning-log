## 今日やったこと
1. リーダブルコード10p読んだ：0.25h
2. Exercism(LanguageList)解いた:1.0h  

## 学び  
1. リスト要素の削除について
   ```java
   languages.remove(languages.indexOf(language));
   ```
   - indexOfメソッドにて要素が見つからなかったときに -1を返し、IndexOutOfBoundsExceptionが発生する
     - languages.remove(Object)を呼び出す形でOK
     - indexOfを使いたい場合は要素が見つからなかったときの例外処理を考慮する

2. リストの先頭要素を取得する実装について
   ```java
   languages.getFirst();
   ```
   - getFirstメソッドは21以降のみ有効,Java17以前では使えないことに注意
   - 空配列の時の例外処理を考慮する。
   - 【補足】空配列をgetFirstで呼び出すとNoSuchElementExceptionが発生する

3. 定数の宣言について
   - private static finalで宣言する慣習
   - しっかりと意識しておく

4. 繰り返し処理における複数要素の比較処理
   - 集合をクラス定数として定義し、ループ処理での比較する形がより良い。
   - StreamAPIのanyMatchを使う実装も有効  
  ```java
    private static final Set<String> EXCITING_LANGUAGES = Set.of("Java", "Kotlin");
    // 比較処理
    public boolean isExciting() {
    for (String language : languages) {
        if (EXCITING_LANGUAGES.contains(language)) {
            return true;
        }
    }
    return false;
    }
  ```

  5. 引数(パラメータ)にnullが入る可能性がある場合、事前にバリデーションチェックを実装するか検討する。

## 所感
1. Mapを使ってリクエストを受け取るイメージができていないので調べる
---

## 今後のTodo
1. UUIDの設定&Instantによる日時設定
2. Exercismの問題を1問解く