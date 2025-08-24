
---

## ✅ SSE（Server-Sent Events）とは？

### 📡 **SSE（Server-Sent Events）**

> クライアント（ブラウザなど）がサーバーに接続して、**サーバーからの一方向のリアルタイム通知**を受け取る仕組み。

* 通信は **HTTPベース**（`Content-Type: text/event-stream`）
* 常時接続を維持しながら、サーバーがイベントを**プッシュ送信**する
* クライアントは **受信専用**（サーバーへの送信は別APIで行う）

---

## ✅ 用語解説

| 用語               | 意味                                | 補足・例                                    |
| ---------------- | --------------------------------- | --------------------------------------- |
| **EventSource**  | クライアント側でSSEを受信するためのJavaScript API | `new EventSource("/sse-endpoint")` で開始  |
| **event-stream** | サーバーからクライアントに送信されるデータ形式           | `text/event-stream` がレスポンスのContent-Type |
| **data**         | 実際に送信されるデータ本文（1イベントあたり1行 or 複数行）  | 例：`data: 映画館情報が更新されました`                 |
| **event**        | イベント名（省略可能）                       | 例：`event: cinemaUpdate` など              |
| **id**           | クライアントが受け取った最後のイベントの識別子           | 自動再接続時に続きから受信するために使用される                 |
| **retry**        | 再接続の待機時間（ms単位）を指定                 | 例：`retry: 5000` は5秒後に再接続                |

---

### 🔄 イベントの送信例（サーバーからクライアントへのメッセージ）：

```
id: 101
event: cinemaUpdate
data: {"cinemaId":123, "name":"渋谷シネマ", "updatedAt":"2025-08-01T12:00:00"}
```

---

## ✅ SSEの仕組みの流れ

1. **クライアント側**が `EventSource` を使ってサーバーに接続
2. **サーバー側**は `text/event-stream` 形式でデータを送信し続ける
3. クライアントはイベントを受け取り、UIに反映
4. 接続が切れた場合は、**自動で再接続**（再送処理も可能）

---

## ✅ SSEの長所・短所まとめ

| 長所              | 短所                           |
| --------------- | ---------------------------- |
| ✅ HTTPベースで実装が簡単 | ❌ 通信は一方向（クライアント→サーバーは不可）     |
| ✅ 自動再接続がある      | ❌ 一部古いブラウザは未対応（IEなど）         |
| ✅ 軽量＆サーバー負荷が低め  | ❌ モバイル回線・ネット断続時の再接続処理には工夫が必要 |

---

## ✅ Spring Boot × SSE の簡易構成イメージ

```java
@GetMapping(value = "/cinema-updates", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
public Flux<String> streamCinemaUpdates() {
    return Flux.interval(Duration.ofSeconds(5))
               .map(i -> "data: 映画館情報が更新されました at " + LocalDateTime.now() + "\n\n");
}
```

```javascript
const eventSource = new EventSource("/cinema-updates");

eventSource.onmessage = function(event) {
    console.log("受信:", event.data);
};
```

---

## ✅ まとめ

| 観点       | ポイント                         |
| -------- | ---------------------------- |
| 用途       | **サーバー→クライアントへの一方向通知**に最適    |
| 特徴       | 軽量・簡単・再接続あり・HTTPベース          |
| 代表ユースケース | ログ配信、チャート更新、一覧リストのリアルタイム反映など |

---

