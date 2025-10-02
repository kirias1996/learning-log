## 今日やったこと
1. 書籍「オブジェクト指向でなぜ作るのか」15p読んだ：0.25h
2. Exercismの問題を解いた:0.5hh  

## 学び  
1. ポリモーフィズム&継承について理解が深まった。
2. JUnitのアノテーション@Tagについて
   - 設定したタグを含めてテスト実行 or テストスキップができることを学んだ。
   - コマンドラインで制御する方法
    特定のタグ(unit)のみ実行
   　```
     ./gradlew test --tests * --info -Djunit.jupiter.tags=unit

     ```
     特定のタグ(slow)を除外(スキップ)
     ```
     ./gradlew test --tests * --info -Djunit.jupiter.excludeTags=slow
     ```
   - build.gradleに設定する方法(includeTagsに含めると実行,excludeTagsに含めると実行対象外)
   ```
     test {
    useJUnitPlatform {
        includeTags 'unit'       // unitタグだけ実行
        excludeTags 'slow'       // slowタグはスキップ
    }
   }
   ```

## 所感
1. JUnitで@Tagについて理解を深めることができた。
　 ローカルでは新規改修のものだけテストする。
　 開発環境や本番環境にリリースする際は全手のテストを実行するなど使い分けができそうだった。
　 タグを複数設定できるかにも今度調べてみたい。
---

## 今後のTodo
1. 技術書を読み進める
2. DBを扱うテストコードを実装したい。
3. 時間があればOSSコードリーディングへ着手する。