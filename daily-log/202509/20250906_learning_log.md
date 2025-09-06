## 今日やったこと
1. Exercism(Calculator Conundrum)を解いた：2h
2. SpringBoot実装の振り返り:1h  

## 学び  
1. Javaで例外をthrowする際のCauseに任意の値を設定する方法
   - 参考サイト
       - https://docs.oracle.com/javase/jp/8/docs/api/java/lang/Exception.html
       - 参照メソッド：public Exception(String message, Throwable cause)
```
  throw new IllegalOperationException(
    "Division by zero is not allowed",
    new ArithmeticException("/ by zero")
);

  ```
   - コンストラクタの第2引数に Throwable のインスタンスを渡す
   - 例外クラスそのものを渡し、うまく実装できずはまってしまった。


2. 例外ハンドリング用テストコードの意味を理解した。
  ```
  assertThatExceptionOfType(IllegalOperationException.class)
    .isThrownBy(() -> new CalculatorConundrum().calculate(33, 0, "/"))
    .withMessage("Division by zero is not allowed")
    .withCauseInstanceOf(ArithmeticException.class);

  ```

   - assertThatExceptionOfType(IllegalOperationException.class)
     - IllegalOperationExceptionが投げられているかを検証
     - 参考サイト：
   - isThrownBy(() -> new CalculatorConundrum().calculate(33, 0, "/"))
     - 例外がthrowされるテストコードを記述する
   - .withMessage("Division by zero is not allowed")
     - 例外のメッセージが「Division by zero is not allowed」であることを検証
   - .withCauseInstanceOf(ArithmeticException.class)
     - cause（原因例外） が ArithmeticException であることを検証
     - causeに new ArithmeticException()を定義する必要がある
   - 参考サイト
     - https://javadoc.io/doc/org.assertj/assertj-core/3.22.0/org/assertj/core/api/Assertions.html#assertThatExceptionOfType(java.lang.Class)

## タグ
#Java #例外ハンドリング　#Exercism