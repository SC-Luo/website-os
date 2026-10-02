# Interaction｜Minimum Viable Rules

狀態：MVR，OS 案例未驗證。基本操作狀態為所有 Tier 的共同品質。

## 狀態與流程

| 情境 | 適用狀態／判斷 |
|---|---|
| 按鈕／連結 | Default、Hover、Focus、Pressed、Active；非同步時 Loading／Disabled 與完成回饋 |
| 表單 | Label、Focus、Filled、Invalid、Submitting、Success、Error、Retry；避免丟失可安全保留的輸入 |
| 空資料／篩選 | Loading、Results、Empty／No results、Clear／Return；說明下一步 |
| 導覽／選單 | Current、Open／Closed、鍵盤及觸控、返回路徑；不用不完整 ARIA pattern 偽裝行為 |
| Dialog／複合元件 | 焦點進出、合理關閉、返回來源；僅在需要時採用 |
| 寫入／重試 | 明確結果、避免非預期重複；不確定完成狀態先 readback，不無限制重試 |

錯誤同時說明發生什麼及可做什麼，不只標紅。公開頁／後台採一致元件與詞彙；內容更新優先區分工作區、未儲存與已儲存，依核准範圍提供預覽，不暗示未實作的永久草稿。

## 選型與驗證

優先 native HTML／既有相容元件；React 路徑依必要性考慮 shadcn／Radix。需要客製前先證明原生／既有元件無法合理滿足需求。

Don't：假按鈕、只有顏色回饋、無實作的成功畫面、單靠停用前端防止競態。

依 [quality](quality.md) 驗證成功、無效輸入、網路故障、重試、焦點與手機；涉及私有資料另執行適用 Security 要求。元件庫通過不代表整個流程通過。
