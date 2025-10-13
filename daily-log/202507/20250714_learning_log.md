## 問題点
MESSAGE_CONTENT_intentが無効だったことにより、Botが想定通り動作しなかった。

エラー文言
```
 [WARN] Attempting to access message content without GatewayIntent.MESSAGE_CONTENT.
Discord now requires to explicitly enable access to this using the MESSAGE_CONTENT intent.
Useful resources to learn more:
        - https://support-dev.discord.com/hc/en-us/articles/4404772028055-Message-Content-Privileged-Intent-FAQ
        - https://jda.wiki/using-jda/gateway-intents-and-member-cache-policy/
        - https://jda.wiki/using-jda/troubleshooting/#cannot-get-message-content-attempting-to-access-message-content-without-gatewayintent
Or suppress this warning if this is intentional with Message.suppressContentIntentWarning()
```


## 原因
Javaコード内でMESSAGE_CONTENTを有効にする記述をしていなかったから。

## 対処法
createDefaultメソッドの後に下記を追加する。
　.enableIntents(GatewayIntent.MESSAGE_CONTENT)

## Discordの設計方針
GatewayIntentで設定できるように分けているのか
→プライバシー侵害や情報漏洩のリスクを減らすため
→本当に必要な機能のみアクセスできる設計方針としている

## Bot開発者が注意すべきこと
①ボットがアクセスできる機能は最小限にとどめること
②本当にその機能を必要としているかしっかりと精査すること。


## 振り返りに関するフィードバック&アドバイス

### フィードバック
1.【問題点】【原因】【対処法】の流れが論理的で、再発防止にも役立つ書き方です。
2.Discordの設計方針やBot開発者の注意点も、背景や意図がしっかり言語化できています。
3.箇条書きや見出しも読みやすく、他の人が読んでも理解しやすいです。

### アドバイス
1. 「なぜそうなったか/どう対処したか」「設計思想や注意点」をセットで振り返ると知識が定着する。
2. 今後のアクションや学びも加えるとよい振り返りになる。