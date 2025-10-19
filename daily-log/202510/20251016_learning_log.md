## 今日やったこと
1. 書籍「すっきりわかるJava入門 実践編」30p読んだ:1h
2. Exercism「NeedForSpeed」の追加テストコードを実装：1h
   - コンストラクタのパラメータ不正に関するテストコードを実装

## 学び  
1. Gitの用語について復習した。
   - cloneするとリモートリポジトリで管理しているブランチがローカル上に作成される。
   - git pullを行うと下記の処理が行われる。
     - リモートのorigin/masterとローカルのorigin/masterを同期(git fetch)
     - ローカルのorigin/masterとローカルのmasterを同期。(get merge)
2. 例外に関するテストコードを複数実装してみた。
   ```
   @Test
    void exceptionTesting() {
        Throwable exception = assertThrows(IllegalArgumentException.class, () -> {
            throw new IllegalArgumentException("a message");
        });
        assertEquals("a message", exception.getMessage());
    }
   ```
   - 参考：[JUnit公式リファレンス](https://oohira.github.io/junit5-doc-jp/user-guide/#writing-tests-assertions)
   - テスト命名（Given_When_Then）を採用してみた。
   - レビューでの改善提案例(3つピックアップ)
     - 失敗系や成功系をNestクラスで分割し、読みやすさを上げる
     - パラメータ化テストで重複データの削減
     - アサ―ト方針(文言一致は変更に弱いため、識別子検証を検討したほうが良い)

## 所感
1. コンストラクタの異常系,正常系をNestクラスでまとめ、意味のあるまとまりにする。
2. 類似データはパラメータ化テストで重複データを削減する
3. 外れ値の検証も実務では必要だと思った。
## 仕事での学び   
1. 業務観点→バッチのテスト観点は連続実行なども検討が必要
2. 既存データを削除する観点も設計時には必要だと学んだ
---

## 今後のTodo
1. 「NeedForSpeed」テストケースの実装
   - 残りのテストケース実装
   - Nestクラスで構造化対応
   - エラーメッセージのアサ―ト方針の検討
   - パラメトリックテストについてチャレンジする。
2. ブランチモデルルールについて調査を少し進める。
   - git-flow
   - gitlab-flow
   - github-flow
   - トランクベース


