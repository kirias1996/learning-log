## 今日やったこと
1. 書籍「すっきりわかるJava入門 実践編」10p読んだ:0.25h
2. JavaGoldのポリモーフィズムの問題を10問解いた。:1h
3. Exercism「NeedForSpeed」の追加テストコードを実装：0.5h
   - 作成したメソッドのテストコードを実装

## 学び  
1. 【業務】equalsメソッドの扱いについて
   - DBから取得したカラムの比較処理をequalsメソッドで実装していた。
   - カラムがnullの場合,NullPointerExceptionが発生するため、事前にnullチェックを行っており、条件が冗長になっていた。
   - `a.equals(b)` の場合、aがnullだと `NullPointerException` が発生する。
   - 定数側を呼び出し元にすることで安全に比較できる（例：`"定数".equals(変数)`）。
   - チームで統一ルールがない場合は、詳細設計書と整合性を取りながら提案してみる。
  ```
  public static final String test = "定数";
  // if文にてnullチェックがなくなり、簡素な条件文となる
  if(test.equals(DB上から取得したカラム)){
    // 処理を記述
  }
  ```
1. bool値に関するテストコードを実装してみた。
   ```
   @Test
    @Tag("task:8")
    @DisplayName("バッテリー消費量と残バッテリーが一致する際の動作検証")
    public void givenBatteryDrainMaxBatteryDrainedFalse(){
        int speed = 10;
        int batteryDrain = 100;
        
        var car = new NeedForSpeed(speed, batteryDrain);
        assertFalse(car.batteryDrained());        
    }
   ```
   - 参考：[参考ドキュメント](https://docs.junit.org/5.0.1/api/org/junit/jupiter/api/Assertions.html#assertFalse-boolean-)

2. Javaの開発においてSQL,Javaの使い分けについて
   - 明日、整理する。
   

## 所感
1. bool値の検証にはassertFalse,assertTrueを使うことを知った。
2. equalsでNullPointerExceptionが発生しない書き方について学べた。
## 仕事での学び   
1. 設計の時にプログラム観点で記述することが大事だと学びました。
---

## 今後のTodo
1. 「NeedForSpeed」テストケースの実装
   - 残りのテストケース実装
2. equalsメソッドの実装について業務で実践してみる


