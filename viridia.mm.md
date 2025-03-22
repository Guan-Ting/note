依賴注入跟 IOC 反轉控制

redis 三種 cache,redis cluster 的優缺點

redis cluster 優點

1. auto sharding with 16,000slot
2. High available
3. decentralization

缺點

1. multi-key operations must be in the same hash slot
2. redis cluster is Complex
   you need spent more time to manage the redis cluster

3. auto sharding
   SQL INDEX 用途是什麼？每個欄位都設 INDEX 會怎麼樣？

SQL N+1 問題

高流量經驗

git flow

## tomcat

- 1. Easy Deployment
- 2. servlet container good compatible with java

## nginx

- high performance
- can be LB and REVERSE PROXY

第一關(全英)

1. 問旅館預約系統怎麼設計
2. nginx 的輪循演算法 知不知道 有沒有用過
3. 跨時間的時間 要怎麼記錄在 db 裡

第二關

- 1.問 thread runnable 差異 問有沒有用過多線程.線程池的概念
- 2.問專案怎麼切分各個功能或是 package 像是 spring 我回答 config entity repository service - 3.問 redis
- 4.白板提 system design 設計短網址系統
- 5.spring @transactional 的優缺點是甚麼 怎麼實現的
- 6.git flow 怎麼跑的

第三關
問 behavior 問題(有沒有失敗的經驗.為什麼要選我們公司..之類的)
