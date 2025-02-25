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
