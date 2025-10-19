## 今日やったこと
1. Javaテストコードの実装：3h
   - Nestedアノテーションを使ってテストのグループ化を行った。
2. Java学習：2h
    実装内容の検討をAIと壁打ち

## 学び  
1. Nestedループを使った構造化
   ```
   @Nested
   class Test{
      @Test
      @DisplayName("throws EmptyStackException when popped")
      void throwsExceptionWhenPopped() {
         assertThrows(EmptyStackException.class, () -> stack.pop());
      }
   }
   ```
   - 非staticな内部クラスでのみ@Nestedが使える。
   - ネストの深さは自由
   - 実務観点で見ると１階層目：テスト観点2階層目正常系,異常系でのグループ化が望ましい。
   - [参考](https://oohira.github.io/junit5-doc-jp/user-guide/#writing-tests-nested)
2. コンストラクタ上でのnullチェック(防御的プログラミング)
   - プリミティブ型の時にはコンパイルエラーが発生するため,nullチェックは不要
   - Integerなどのラッパークラスであればnullを確認する。
     - Objects.requireNonNullで代入 + nullチェックを1行で実装することができる。
   ```
   Integer value = Objects.requireNonNull(parameter,"エラーメッセージ");
   ```
   - null代入を許可しないことを明示化できる。
3. 実務の開発方針案の壁打ち(バッチ製造に関するTipsをISSUE等にまとめておく)
- [参考](https://chatgpt.com/share/68f479d0-c2c8-8005-8016-6e5e66b9c138)
   

## 所感
1. @Nestedを使うケースについて整理&実装できた。
  - JUnitのユーザガイドサイトを見ながら実装できるようになったのが良かった。
2. OSSのJavaコードリーディング用のリポジトリを構築した。
   - テンプレート等を用意してすぐに始められる準備が完了した。
3. 1クラスのテストを実装しているだけなのに考慮することが多く勉強になる。
   - 納期が厳しい時にテストケースの取捨選択が大変だなと思った。
---

## 今後のTodo
1. 「NeedForSpeed」テストケースの実装
   - 正常テストケースの境界値対応
   - エラーメッセージのコード化対応(ResourceBundle)
   - @ParameterizedTestで境界値,正常値を束ねてテスト実行する。
   - assertDoesNotThrowの実装
     - RaceTrackコンストラクタの正常テストに採用予定
     - getter等がないクラスでパラメータ不正がなく、例外が投げられないことの検証に利用する。 
2. JavaGoldの資格勉強


