# 台北通後台

## 權限管理

- 系統使用者管理
- 發卡機關管理
- 卡證管理
- 機關與部門管理
- 系統使用者停用紀錄

## 卡證管理

- 匯入會員卡證資料

- 卡證會員資料

- 卡證授權服務管理

- 卡證標籤管理

## 會員管理

- 會員資料查詢
- 新增一般會員
- 匯入會員
- OCR 註冊申請列表
- 會員代碼轉換會員資料

## 服務管理

## 訊息

- 歷史訊息與訊息排程列表

- 新增訊息

- 查詢批次派送訊息設定

- 匯入批次訊息檔案

- 用戶主題列表

- 新增用戶主題綁定

## 上稿管理

- 優惠券管理
  - Coupon
  - CouponDispatch
    - USERRECEIVECOUNTERROR(-5),每人獲得張數有誤
    - NOTENOUGHPIECE(-4),剩餘折價券不夠發送
    - NOCONDITION(-3),沒有條件，不支援群發
    - DELETE(-2)
    - FAILED(-1)
    - RETRY(0)
    - WAITING(1)
    - TRANSPORTING(2)
    - SENDED(3)
  - CouponDispatchRecord
    - UKNOWNERROR(-1),
    - NOTUSE(0),
    - USED(1),
    - EXPIRED(2),
    - COUPONEXPIRED(3), // 超過折價券停用或超過領取時間
    - COUPONLIMIT(4), // 折價券數量不足
    - COUPONUSERLIMIT(5), // 超過個人領取限制數量
    - USERNOTEXIST(6), // 找不到這個使用者
    - CREATEFAILED(7); // 寫入折價券時 DB 異常
  - CouponUsedRecord
    - RECEIVE("R"),
    - USED("U"),
    - AMEND("B"),//補單
    - DELETE("D");
    - CouponPaidRecord
- 優惠券發送紀錄
- 優惠券使用紀錄
- 商家管理
- 常見問題列表
- 新增常見問題
- 活動訊息列表
- 新增活動訊息
- 輪播列表
- 教學管理
- iSSO 首頁公告設定

## 報表

- 意見回饋
  - 使用者透過此功能填寫意見回覆
- 系統紀錄
  - 可查詢數位足跡
- 身分驗證服務紀錄

- 卡證 API 發送紀錄
- 會員介接紀錄
- 戶役政查詢紀錄
- 匯出戶役政稽核報表
- 統計報表
- 參數設定
- 外部網址白名單
- 凍結戶記錄
- 會員查詢紀錄

# 批次排程

- 戶役政每月更新紀錄
- 用戶主題綁定
- 用戶最後登入紀錄
- Onesignal 用戶記錄更新
- 自動停用過期 SysUser 帳號
