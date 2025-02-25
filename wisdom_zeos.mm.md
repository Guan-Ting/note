# 面試知識點與問題整理

## 1. Public 與 Private 定義與區別

- 知識點
  - **Public**:
    - 所有類別可存取。
    - 用於對外公開的方法或變數。
  - **Private**:
    - 僅限於本類別內存取。
    - 用於封裝內部邏輯，保護數據。
- 可能的面試問題

  - Public 與 Private 的區別是什麼？
  - 什麼情況使用 Private？
    - 提高安全性
    - 封裝資料，讓只有該 class 可以去存取它
  - modifer 有哪些 (如 default, protected) 並比較它們？

    - public
    - protected
    - default
    - private

    同類別 同套件 不同套件子類別 不同套件非子類別 皆可以存取

## 2. 壞味道 (Bad Smell) 程式碼分析

- 知識點
  - 定義編碼中的壞味道 (bad smell)
    - 示例如：
    - 不當的耦合關係
    - 重複代碼(duplicated code)、
    - 長方法(long method)、
    - 過多參數(too many parameters)、
    - 神物件(god object)。
  - 工具輔助：SonarQube 分析常見問題。
- 可能的面試問題

  - 如何發現程式壞味道？
  - 如何修正？(ex: refactor)
  - 示範程式碼問問題：

    ```java
    class Rectangle {
        public int length;
        public int width;

        public int calculatePerimeter() {
            return 2 * length + 2 * width;
        }
    }
    ```

    - 問題：有哪些潛在壞味道？應該怎樣改？

## 3. 最近用過的設計模式

- 策略模式

  - 將行為封裝，透過行為 interface，各種策略去實現 interface，讓 context 裡可以依據不同策略有對應行為
  - 最近工作用的到需求為依據不同個資作隱碼規則
  - 例如身分證 手機 姓名等

  好處:可以大量消除 IF/ELSE

- 知識點
  - 常見設計模式
    - **Singleton**: 確保一個類只有一個實例。
    - **Factory**: 封裝對象生成邏輯。
    - **Builder**: 拆分複雜物件的建造過程。
    - **Observer**: 訂閱機制，通知多個觀察者。
  - 使用場景範例
    - Singleton 解決全局配置唯一性。
    - Factory 提高耦合度。
- 可能的面試問題
  - 你用過的設計模式？為什麼選它？
  - 從零設計一個模式的實現？
  - 什麼情況使用 Singleton 是不恰當的？

## 4. 基本的資料庫語法 (SQL)

- 知識點
  - 基礎查詢
    - `SELECT`: 查詢資料。
    - `WHERE`: 條件篩選。
    - `JOIN`: 關聯表。
    - `GROUP BY`: 分組聚合。
  - 修改操作
    - `INSERT INTO`
    - `UPDATE`
    - `DELETE`
  - 索引與效能優化
  - mysql: LIMIT 10 OFFSET 0
  - MSSQL:OFFSET 0 ROWS FETCH NEXT 20 ROWS ONLY

## 5. Unit Test 設計測試案例

- 知識點
  - 測試案例設計
    - 正確情境測試。
    - 邊界情況測試。
    - 異常情境測試。
- 可能的面試問題

  - 某功能：設計測試案例的思路？
  - 如何確保單元測試覆蓋率高？
  - 示例題：

    - 功能敘述：計算兩數相加減的結果。
      - 測試案例：
        1. 輸入 2 和 3，期望結果 5。
        2. 輸入 0 和負數，期望結果為負數。

  - 例題
    - 一個 Caculator 方法 裡面試 a/b，如果 b 為 0，則 throw IllegalArgumentException
    - 測試案例
      - 普通 CASE
      -

## 6. 設計堆疊類別

- 知識點

  - 資料結構：堆疊的原理與應用。
  - 支援的操作：`push`、`pop`、`top`、`getMax`。
  - 設計堆疊實現 (Java 範例)：
  - ```java
    class MaxStack {
        private Stack<Integer> stack = new Stack<>();
        private Stack<Integer> maxStack = new Stack<>();

        public void push(int x) {
            stack.push(x);
            if (maxStack.isEmpty() || x >= maxStack.peek()) {
                maxStack.push(x);
            }
        }

        public int pop() {
            if (stack.peek().equals(maxStack.peek())) {
                maxStack.pop();
            }
            return stack.pop();
        }

        public int top() {
            return stack.peek();
        }

        public int getMax() {
            return maxStack.peek();
        }
    }
    ```

- 可能的面試問題
  - 如何保證 `getMax` 的效能為 O(1)？
  - 是否能擴展其他函數？

## 7. Pool (池化)

- 知識點
  - 定義：
    - 有效管理對象的重用，減少頻繁創建和銷毀的資源消耗。
  - 例子：
    - 資料庫連線池。
    - 線程池。
  - 實現原則：
    - 池容量限制。
    - 資源回收機制。
- 可能的面試問題

  - 池化技術的優缺點？
  - 如何設計一個連線池？

  池化為管理資源的重用，系統可避免重複的銷毀與獲取資源，常見於

  - 連線池
  - 線程池

  好處為

  - 減少頻繁創建和銷毀資源的性能損耗。
  - 提升資源使用效率。
  - 控制最大資源數量，避免系統過載。

  -

## 8. Java Interface 與 Abstract Class

- 知識點
  - **Interface**:
    - 定義方法的契約，多重實現。
    - 沒有狀態/變數。
    - 制定規格，貼標籤的概念
    - java 8 後 interface 有 default 方法，獨立於一般的抽象方法
      - 好處，往前相容，實作介面的 class 不用再 override
      - 一個 interface 可以有多個 default
  - **Abstract Class**:
    - 類的抽象，高階行為封裝。
    - 可以有狀態/具體方法。
    - 父類別與子類別有 is a 的關係
- 可能的面試問題
  - 抽象類與介面的區別？
    - 抽象類別不能直接實體化，專門要給子類別繼承，java 的缺點是無法多重繼承，若繼承抽象類別就不能再繼承別的
  - ## 多繼承問題如何解決？
  - 假如要傳遞多個功能，該選什麼？ 該用 interface

## 8.SOLID

- S:Single-responsibility principle

- O:Open–closed principle

- L:Liskov substitution principle

- I:Interface segregation principle

- D:Dependency inversion principle

---
