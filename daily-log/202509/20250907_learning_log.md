## 今日やったこと
1. リーダブルコード12章読了：0.5h
2. SpringBoot実装演習:3h  


## 学び  
1. REST APIでの日付バリデーション実装について
   - REST APIでは @JsonFormat / カスタムデシリアライザを利用する。
   - @Pattern
     - DTOがStringのときだけ使う最後の手段。REST APIでは非推奨（型が曖昧になりがち）。
   - @DateTimeFormat
     - 主にフォームバインディング（@ModelAttribute）向け。JSON（@RequestBody）はJacksonなので効果が薄い/無し。
   - @InitBinder
     - フォーム系に利用する想定。JSONには基本使わない。

   - 参考サイト
       - https://www.baeldung.com/jackson-jsonformat
       - https://github.com/fasterxml/jackson-annotations/wiki
       - https://fasterxml.github.io/jackson-annotations/javadoc/2.7/com/fasterxml/jackson/annotation/JsonFormat.html

   - @JsonFormatを使用したバリデーションを実装
  ```
  @JsonFormat(pattern = "yyyy-MM-dd")
	private LocalDate dueDate;
  ```


2. アプリで日時形式を扱う方針について
   - 日付形式は1つに絞るのがベストプラクティス
   - APIリクエスト時に利用者がどの形式を指定すべきか迷わない
   - 日時形式が1つに定まるため、テストがシンプルになる
   - 他システムに連携する際もISO標準形式(yyyy-MM-dd)が扱いやすい

3. RESTAPIのレスポンス形式について
   - UPDATE時のリクエスト/レスポンス
     - リクエストメソッド
       - PUT:全置換
       - PATCH:部分更新
     - レスポンス形式
       - ステータスコード(200) + 更新後のJsonレスポンス →実務でよくつかわれる
       - ステータスコード(204) + NoContent
   - DELETE時(単体削除)のHTTPステータス
     - 成功時:204 + NoContent
     - 削除レコードなしの時、404  
 
## 所感
1. RESTAPIのレスポンス形式について理解が進んだ
2. 日付形式を使う際のベストプラクティスを学べた。


## 明日のTodo
1. Exercism(Squeaky Clean)を解く

  






## タグ
#Java #例外ハンドリング　#Exercism