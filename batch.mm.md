# Batch

## Quartz

- JobStore

  - RamStore
  - JDBCJobStore
  - TerracottaJobStore

- 配置 Cluster

  - isClustered 設為`true`
  - instanceId 沒有規範的話設為`AUTO`

- 元件
  - Job
  - JobDetail
  - Trigger
  - Scheduler
  - 議題
    - misfire
      - 為什麼會出現 misfire
        - 系統時間出現變化(建議使用 NTP)
        - 任務處理時間過長
        - Quartz 調度器暫停或終止，而觸發器的計劃執行窗口已過
      - 補償機制
        - withMisfireHandlingInstrucetionDoNothing():錯過的不再補償，後續正常執行
        - withMisfireHamdlingInstructionFireAndProceed():默認值，錯過的全部合併成一次，並立即補償(即使任務終止時間已到達)，然後後續正常執行
        - with MisfireHandlingInstructionIgnoreMisfires():錯過的全部補償，然後後續正常執行
- 持久化

# QuartzJob

## 接口

- /healthcheck
- /list 顯示所有排程
- /pause 暫停
- /pauseAll 暫停所有排程
- /start 啟動
- /resume 恢復排程
- /resumeAll 恢復所有排程
- /delete 刪除指定排程
- /update 更新所有排程
- /add 新增排程
- /getAllJob
- /uploadJob
- /test 測試接口
