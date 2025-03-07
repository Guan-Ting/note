# 台北通商家網站

- 修改票卷 javascript 邏輯
- 將下載店家的貼紙 放到 cdn
- 將使用者的狀態做成 jwt 放到 session storage 並儲存到資料庫 (裡面含有使用者的資訊 及 哪個時間操作到哪步驟)
- 部屬到兩台 server

- 到 app 登陸 熊好卷 queue it > F5 > 7 台 server

# 資料庫加密

- 目的:將身分證手機等資訊加密
- 對稱式金鑰 AES key
- 所有系統 都要固定用同一把 key 同個偏移值(iv) 才能 互相解開

# 台北通後台-授權服務

- 從後台設定服務協議

- 設定授權服務

- 讓 app 在打開我的服務時 會先有服務協議 讓 user 決定是否授權個資到 web view

- 用 commons-csv 實作報表

# 台北通 redis

- 知識點
- 資料結構
  - String
  - Hash
  - list
  - set
  - sorted set
- 內存淘汰模式
  - redis 基於 內存去做淘汰 key
  - 基於 ttl 時間去做淘汰 key
  - 手動去淘汰 key
- redis 三種緩存炸掉的問題

  - 緩存雪崩 cache Avalanche:因為 ttl 設定時間都相同，因此緩存在同一時間都失效而讓 request 都進入 db
  - cache invalid:針對熱點 key 因 ttl 到期，因此大量請求就進入 db 導致效能下降，解決方式:熱點 key 永不過期

  - cache penentration:
    戶請求的數據既不在緩存中，也不在 db 中，因此若有大量這種請求時，也會對 db 有壓力
    解決方案:如果請求為空的話，這空值也存到緩存
    或是使用或是使用 bloom filter
  - bloom filter:
    布隆過濾器就像一塊用來標記數據的黑板，你只記位元，不記原始數據。當一個數據來查詢時，如果對應的位置沒被標記，就肯定不在；但如果標記了，則可能存在

  - redis 儲存方式:
  - aof: 文本形式持久化在硬碟中，可靠性高，類似一行命令一行命令存下來
  - rdb: rdb 快照，間隔時間會生成快照，省資源| 性能較高，能快速啟動
  - master-slave 間傳訊:如果 master 剛與 slave 聯繫上 MASTER 會建立一次 RDB 快照給 SLAVE，後續則以命令的方式 ASYNC 到 slave，如果出現大規模網路延宕，會依據要 async 的
    數量，如果差距太多的話，master 會再建立一次 rdb 快照給 slave

# 台北通簡訊 & 推播 onesignal

# 台北通後台單一登入

用台北通 app Oauth 登入帳管系統，帳管系統會用 jwt 送 request 到台北通後台介面，藉由 jwt 裡面的 token 再跟帳管系統交換回 user 帳號和部門資訊，只要全部符合後台登陸的內容 即可 登入

# 南山 saml

- 1.申請憑證，提供 cer 給 IDP
- 2.填寫 XML 給 IDP 註冊的兩個接口位置(/acs 與 /logout)
- 3.實作 SP 的登入接口，導頁至 IDP 提供的/SSO 位址(傳入 SAMLRequest)
- 4.實作[POST] /acs 接口，用於接收 IDP 提供的登入驗證結果(SAMLResponse)並解析登入者
- 5.實作 logout 接口

# 南山

- spring boot 跟 Vue 打包在一起
- mvc config 設定將靜態網頁指向 static
- 把打包的 Vue 程式放在 resource/static 底下
- controller based url 路徑 forward 到 index.html

# 困難

- 不好解的問題 1.當 SA
- 2.card api 問題
  - 2 小時約 12 萬筆的請求
  -
