# SQL

## count 使用

- count(\*):會計算到 null
- count(1):會計算到 null
- count(主鍵):計算不為 null 的數量

## 優化查詢

- 關聯列上建立索引

  - 隨著 CRUD 索引結構會逐漸變得不連續，因此要索引重建
  - MSSQL 使用- DMV 查詢碎片化程度
  - 使用 rebuild 指令 重建索引

- 提高索引覆蓋率
- 減少 SELECT 的字段數量
- 使用 where 界定範圍
- 以小表驅動大表

  - **數據掃描量會減少**

- 使用子查詢 EXIST / NOT EXIST
- 使用分布查詢和臨時表

## EXISTS vs IN

- EXISTS 系列會 對外表 做 LOOP 循環
- not IN 要小心 若 value 為 NULL 的情況
- 子查詢若比外表大 建議用 EXISTS
- 子查詢若比外表小 且有索引時用 IN 確實較好，其他可能用 EXISTS 會更好

- 為什麼要索引

  - 索引相當於書本的目錄，大部分資料庫索引是以 b-tree 作為資料結構，可以避免全表掃描，優化排序，但隨著 insert 及 delete update 會影響索引結構，進而產生碎片話，因此透過 mssql 透過 dmv 查詢索引碎片化程度，看狀況要 rebuild 索引

- 可以每一個都加上索引嗎
  增加索引會有額外的存儲空間，每個都也會影響最佳查詢時間，就好比書本的目錄每一頁都有一筆的話 那乾脆不要有，一般會以唯一值 或 group by order by 的值

# acid

- A:原子性 交易必須是 全有或全無 spring 提供 @Transactional 來保證原子性。redis 雖然是單線程可提供原子性，但她無法 rollback

- C:一致性，在交易完成後，資料庫要從一個一致的狀態轉換到另一個一致的狀態，例如從 A 帳戶匯款到 B，你從 a 帳戶轉了 100 元，b 帳戶就要多 100 元

- I:隔離性:
- 資料庫中有不同的隔離級別 (Transaction Isolation Levels) 例如：

  - **Read Uncommitted**：允許讀取未提交的數據（可能有髒讀）。
  - **Read Committed**：只能讀取已提交的數據（避免髒讀）。
  - **Repeatable Read**：確保同一交易內多次讀取的數據一致（避免不可重複讀）。
  - **Serializable**：最高隔離級別，防止幻影讀。

- D:持久性:- 一個交易完成後，其對數據的變更必須被永久保存

# race condition

- 平行處理
- 對同一個資源同時進行存取操作
- 解決方式
  - 使用樂觀鎖 Optimistic 用 version 的字串決定要不要更新
  - 用悲觀鎖 Pessimistic
  - 事務隔離級別 I 的概念

# dead lock 解決方式

- 常見模式:兩個交易各自鎖住資源又要對方的資源導致死結

- 解決方式:

  - 鎖增加超時的設定，時間到了就釋放 Add timeout settings to the lock

  - 設定兩個交易的訪問順序 set the order for the transaction

- 預防方式:
  - 縮短交易時間跟範圍
  - 固定順序訪問資源

# 分頁問題

- 常見 百萬筆以下的話
  - 可以用 select l.\* From Logging l inner join

(select id FROM Logging

ORDER BY endTime DESC

OFFSET 0 ROWS FETCH NEXT 10 ROWS ONLY) as tmp on tmp.id = l.id

- 千萬筆以上的話可以考慮用自增 id 或者是把上一個的 lastupdateTime 當成查詢條件
  SELECT TOP 10 \*
  FROM Logging
  WHERE [endTime] <= getDate()
  ORDER BY [endTime] DESC;

  SELECT TOP 10 \*
  FROM Logging
  WHERE [endTime] <= '2025-03-05 18:21:14.0670000'
  ORDER BY [endTime] DESC;

深分頁

# 主鍵

- auto increment
- uuid v4 (無序)
- uuid v7 (有序)
  - 避免 Y2K38 問題 - 因為他使用 48 位元紀錄時間戳記
  - 應對分布式或時區問題 - 因為是使用- UTC 時間作時間戳記所以沒問題
    -
