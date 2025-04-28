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

- ## Thread pooling:

- ## CH6.併發挑戰與解決方案
  - synchronized
    - 對象鎖而非方法鎖：Java 同步機制鎖定的是對象，而非方法。
    - 不同方法，相同鎖：對同一個對象的不同同步方法使用的是同一個鎖。
    - 性能考量：雖然同步能保證線程安全，但也可能導致線程等待，降低程序性能。
