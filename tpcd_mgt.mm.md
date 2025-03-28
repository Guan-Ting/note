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

- 授權服務
- 設定熱門服務
- 設定使用者預設服務
- 設調服務分類
- 設定 Webview 服務
- 設定服務協議
- 設定服務協議範本
- 設定服務標籤頁

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

- 用戶主題綁定 job5905 0 _/3 _ \* \* ?
- 會員推播分組 fcm-topic-job 0 0 _/2 _ \* ?

- 停管推播資料匯入 DB message-job 0 0/10 \* \* \* ?
- 用戶最後登入紀錄 UserLastAccessJob 0 0 3 \* \* ?
- 批次刪除 NAS 資料 nsa-clear-job 0 0 0 ? \* MON

- 用戶主題解除綁定 job8306 0 _/3 _ \* \* ?
- Onesignal 用戶記錄更新 TagUpdateJob 0 0/3 \* \* \* ?

- 戶役政每月更新紀錄 HouseHoldQueryExportJob 0 30 0 1 \* ?
- 自動停用過期系統帳號 SysUserFreezeJob 0 0 1 \* \* ?

- OneSignalGetCSVURLJob OneSignal 取得下載 URL 0 0 _/3 _ \* ?
- OneSignalDownloadCSVListJob OneSignal 下載使用者名單 0 10 _/3 _ \* ?
- OneSignalDeleteEmptyUserJob OneSignal 刪除空頭帳號 0 30 _/3 _ \* ?

# API

- 卡證 API:/tpcard/rest/v3.0.0/cardservice/
  - 一次只能發給一個使用者
- 派券 API: /tpcard/rest/v1.1.0/coupon/dispatch
  - 一次只能發給一個使用者
- 發送個人訊息 API:/tpcard/rest/v1.1.0/personalmsg
  - 一次只能發給一個使用者
- 會員批次建立 API:tpcard/rest/v2.2.0/member

- 取號系統 API(取號系統專案)
  - /tpeaccount /api /v1.0.3 /booking 預約/取得已存在帳號
  - /tpeaccount /api /v1.0.3 /cancel 取消預約
  - /tpeaccount /api /v1.0.3 /confirm 確認預約帳號
  - /tpeaccount /api /v1.0.3 /register 新增/取得已存在帳號
  - /tpeaccount /api /v1.0.3 /update 員⼯狀態更新
