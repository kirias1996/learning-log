## 今日やったこと
1. Javaテストコードの実装：1h 
   - ParameterizedTestアノテーションを使ったテストを実装してみました。 
2. JavaGold勉強：1.5h
   - Iteratorの機能に関する理解があいまいだったので復習&コード実装してみる。

## 学び  
1. ParameterizedTestを実装した。
```
   @ParameterizedTest
   @CsvSource({ "foo, 1", "bar, 2", "'baz, qux', 3" })
   void testWithCsvSource(String first, int second) {
    assertNotNull(first);
    assertNotEquals(0, second);
  }
```
   - まとめるべき粒度はテスト観点や分岐が同じもの
   - @MethodSourceや@CsvFileSourceなどもあるので他の機会で試してみる
   - [参考](https://oohira.github.io/junit5-doc-jp/user-guide/#writing-tests-parameterized-tests)
2. DBMSがメモリを搭載している理由
  - パフォーマンス向上:SQLの実行速度を速くするため  
  頻繁にアクセスするデータをメモリに保持することでディスクを解さずにメモリからのみのアクセスが可能。
3. 業務でのテスト仕様書作成に関する学び
   - カラム名などは見切れないようにする
   - すべて一致欄を作ってCOUNTIF等で全一致しているかを確認する

   

## 所感
1. @ParameterizedTestを使ったテストコードが実装できた。
  - かなりシンプルに書けるので手動テストよりとてもやりやすそうだった。
  - 実務では100件とか出てくる可能性もあるので@CsvSourceFileを使うのかなと思いました。
  - @MethodSourceや@CsvFileSourceの使い方にも慣れていきたいと思いました。
2. StringUtilsのisBlankメソッドを分析した。
   - 早期returnやnullセーフの実装が行われていた。
   - Java標準メソッドもたくさん使われているので仕様を学ぶいい機会になりそうだった。
   - もう少しオブジェクト指向(ポリモーフィズム等)の設計についても学ぶべきか壁打ちしたい。
3. JavaGoldの勉強でIteratorの理解があいまいだと感じた。
   - 理解を深めるため、AIにコーディング課題を出してもらって解くことにした。
---

## 今後のTodo
1. テストケースの実装
   - 正常テストケースの境界値対応
   - エラーメッセージのコード化対応(ResourceBundle)
   - @ParameterizedTestで@MethodSourceや@CsvFileSourceを使ってテスト実行する。 
2. JavaGoldの資格勉強
   - Iteratorを使ったコーディングにチャレンジする
3. オブジェクト指向設計に関する知見を深めるために必要なことをAIと壁打ちする。


