## 概要
SpringBootでのh2DBの環境設定手順を記述

## 環境設定手順
1. build.gradleに依存関係を追加
```
implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
runtimeOnly 'com.h2database:h2'

```
2. application.ymlにDB接続設定を記述
```
spring:
  datasource:
    url: jdbc:h2:mem:taskdb;MODE=PostgreSQL;DATABASE_TO_LOWER=TRUE;DB_CLOSE_DELAY=-1
    driver-class-name: org.h2.Driver
    username: sa
    password:
  jpa:
    hibernate:
      ddl-auto: update   # dev用（本番は使わない）
    properties:
      hibernate.format_sql: true
  h2:
    console:
      enabled: true
      path: /h2-console
application.name: task_app
logging.level.org.hibernate.SQL: debug

```
3. SpringBootを起動
  - 「http://localhost:8080/h2-console」にアクセスし、「Connect」を押下しログインできることを確認
  - 
4. クラスに処理を記述
  - Repositoryインターフェースの実装
  - Entityクラスの実装
  - Controllerクラス,Serviceメソッドの呼び出し処理を変更
  - 各処理の記述は割愛→GitHubのリンクを完成し題張り付ける。