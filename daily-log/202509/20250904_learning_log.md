## 今日やったこと
1. リーダブルコード9章読了：0.25h
2. Java(SpringBoot課題実践):1h  

## 学び  
1. Controllerクラスで400エラーを出す方法(バックエンドのみ)
   - 【前提】実行メソッドに@RequestBody @Valid：REST APIでのバリデーションが可能
   - バリデーション失敗時はMethodArgumentNotValidExceptionが返ってくる  
     @ControllerAdviceを付与したクラスにて400とエラーレスポンスを返す。
   - BindingResultを使う方法もあるが,エラーレスポンスを返し、例外は発生しない


2. ControllerクラスでJsonレスポンスを返却する方法
   - @RestControllerを付与する。
   - Locationヘッダを付与した構成が好ましい。
   - build()はボディなし専用のメソッド
   ```
   URI location = URI.create("/tasks/" + createdId);
   return ResponseEntity.created(location).body(responseDto);
   ```


## 所感
1. バリデーション失敗時に例外を発生させ、@ControllerAdviceでエラーレスポンスを返すしようとする。
2. Jsonレスポンスの返却方法について理解することができた。
---

## 今後のTodo
1. OpenAPI/Swaggerを用いたAPI仕様書反映の自動化
2. 正常レスポンスを受け取る処理を実装
3. 異常系は@ControllerAdviceにて例外をキャッチする手法を取り込む。

## タグ
#Java #SpringBoot　#RestController　#API設計