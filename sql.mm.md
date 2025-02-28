# SQL

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
- 子查詢若比外表小 建議用 IN

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
