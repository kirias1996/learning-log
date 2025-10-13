## 今日やったこと
1. リーダブルコード10p読んだ：0.25h
2. SpringBoot課題実践(パッケージ構成検討&API実装着手):1.0h  

## 学び  
1. バックエンドのみとフォームありの引数の使い分け
   - バックエンド
     - JSON形式のリクエスト(RESTAPI)→ @RequestBody × @Valid
     - 不正入力はMethodArgumentNotValidExceptionで400エラーを返す。
   - フォームデータやクエリパラメータ
     - @ModelAttribute + BindingResult
2. UUIDの実装
   - UUID uuid = UUID.randomUUID();
   　uuid.toString();
   - 制約がない場合はメソッドの戻り値をLongにしておくのが無難
3. 日時にInstantを扱う場合のベストプラクティス
   - Instant.now(Clock.systemUTC())

## 所感
1. Mapを使ってリクエストを受け取るイメージができていないので調べる
---

## 今後のTodo
1. UUIDの設定&Instantによる日時設定
2. Exercismの問題を1問解く