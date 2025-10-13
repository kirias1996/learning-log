

---


# Map → StreamAPIへの変換処理の整理

## ✅ 実装コード

```java
List<String> displayResults = buyBookByemployees.entrySet().stream()
    .sorted(Map.Entry.<String, Integer>comparingByValue(Comparator.reverseOrder()))
    .map(Map.Entry::getKey)
    .collect(Collectors.toList());
```

---

## ✅ 実装の流れと目的

### ① MapをStreamに変換

```java
buyBookByemployees.entrySet().stream()
```

* `Map` は直接 `stream()` を使えないため、まず `entrySet()` で `(key, value)` ペアの集合に変換。
* 得られる型は `Stream<Map.Entry<String, Integer>>`。

---

### ② ソート処理

```java
.sorted(Map.Entry.<String,Integer>comparingByValue(Comparator.reverseOrder()))
```

* `Map.Entry` の値（`Integer`）を降順でソート。
* `<String, Integer>` の型パラメータは、型推論が曖昧な場合の補助に使う。

---

### ③ `.map()` によるキー抽出

```java
.map(Map.Entry::getKey)
```

* 各 `Map.Entry` を `String` 型（キー）に変換。
* この時点で `Stream<String>` に。

---

### ④ `.collect(Collectors.toList())` によるリスト化

```java
.collect(Collectors.toList());
```

* 結果を `List<String>` として格納。
* **forEachでの出力だけでもよい**が、リストにしておくことで以下のメリットがある：

---

## ✅ リスト化を選んだ理由

* 将来的に **別メソッドで再利用**しやすくなるため。
* **単体テストが容易**になる（戻り値に対して検証可能）。
* 表示以外にも、APIレスポンスやファイル出力など柔軟に対応可能。

---

## ✅ フィードバック・補足

* `.entrySet().stream()` → MapからStreamに変換する代表的パターン。
* `.sorted(...).map(...).collect(...)` のような**中間処理＋終端処理**の流れを意識するのがポイント。
* 実務では、**可読性や責務の分離**を重視し、`List`にまとめる形が推奨される場面が多い。
* `forEach(System.out::println)` による直接出力も可能だが、**再利用性・保守性を考えるとcollectが優位**。

---

## ✅ 今後の発展的な学習候補

* `filter()`：条件による絞り込み
* `toMap()`：StreamからMapへ再構築
* `groupingBy()`：グルーピング集計
* `peek()`：デバッグ用の中間出力

```
