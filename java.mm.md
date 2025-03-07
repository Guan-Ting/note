# Java

## java 8

- localDateTime API

## java concurrent

- thread vs process

  - mutithread 跟 mutiprocess 的差異

- Thread basic

  - 甚麼是 daemon thread?
    - 設定為 daemon thread 時，會隨著使用者執行緒的停止而自動退出
  - 合併線程

    - join():阻塞當前線程
      - 1.  最好設定超時時間 ex .join(200);

  - 性能優化: 未來詳見 CHAPTER4.性能優化
    - latency
    - throughput
    - 我們可以永遠考慮併行嗎? 答案是 no ，mutithread 固定會付出一些成本，最好做 single & mutithread 比較圖
