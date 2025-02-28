# Spring

## Spring MVC

- BindingResult

## Spring
  - 核心概念
    - aop
    - ioc
    - bean的生命週期 
  - 一個resquest進來執行順序 
    - filter
    - interceptor
    - aop
      - 1.日誌
      - 2.避免重複點（幂等性檢查）
      - 3.api key 驗證



  
## Spring Boot 
- springSecurity
  - 跨域問題

# 考題

 ## 一個resquest進來執行順序

  - 1. **客戶端發送 HTTP 請求**
  - 2. **Servlet 容器接收請求**
  - 3. **Spring Security Filter Chain 處理請求**
  - 4. **DispatcherServlet 接管請求**
  - 5. **Handler Mapping 定位 Controller**
  - 6. **Handler Interceptor **
  - 7. aop pointcut
  - 8. 進到controller

 ## N+1問題

  - 導致原因:設定fetch lazy時 ，當要查詢關聯的屬性時，會觸發join而有額外的查詢
  - 使用原生sql
  - 使用 `IN` 子查詢批量抓取關聯數據，減少單筆獨立查詢








  - filter
  - interceptor
  - aop 