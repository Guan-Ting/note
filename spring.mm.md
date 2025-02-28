# Spring

## Spring MVC

- BindingResult

## Spring

- 核心概念
  - aop
  - ioc
  - bean 的生命週期
- 一個 resquest 進來執行順序
  - filter
  - interceptor
  - aop
    - 1.日誌
    - 2.避免重複點（幂等性檢查）
    - 3.api key 驗證

## Spring Boot

- springSecurity

  - CORS 在 spring secuirty 中 於 corsFilter 去設定 可以通過的 網域 http 方法 還有 http 的 header
  - CSRF 如果開啟的話

  - Authentication & authorization
    Authentication 為 who you are 透過 傳統帳密 或是 saml 的方式 決定你的身分
    -authorization 你是甚麼角色，你可以幹嘛 通常會用 定義 url 跟 角色之間的關係

  - DDOS
  - XSS:- 藉由前端注入惡意的 JavaScript 代碼

    - 1. **Stored XSS** : user 可填表格或 text 的功能
    - 2. **Reflected XSS** : URL 裡面可能有 javascript 程式
    - 3. 1. **DOM 型 XSS**
            解決方式:透過過濾或轉譯不要讓惡意 js 執行

  - SQL Injection: 輸入欄位中插入惡意的 SQL 語句，進而 SELECT 或 DELETE 資料
    解決方式:用 PREPARE STATEMENT 佔位符 或 ORM

# 考題

## 一個 resquest 進來執行順序

- 1. **客戶端發送 HTTP 請求**
- 2. **Servlet 容器接收請求**
- 3. **Spring Security Filter Chain 處理請求**
- 4. **DispatcherServlet 接管請求**
- 5. **Handler Mapping 定位 Controller**
- 6. **Handler Interceptor **
- 7. aop pointcut
- 8. 進到 controller

## N+1 問題

- 導致原因:設定 fetch lazy 時 ，當要查詢關聯的屬性時，會觸發 join 而有額外的查詢
- 使用原生 sql
- 使用 `IN` 子查詢批量抓取關聯數據，減少單筆獨立查詢

## 如何實現批次儲存

- dont:spring data jpa 的 saveAll 是迴圈繞
- do: jdbctemplate batchupdate
- do: spring data jpa hibernate 提供的 batchsize

- filter
- interceptor
- aop
