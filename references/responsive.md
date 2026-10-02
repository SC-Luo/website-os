# Responsive｜Minimum Viable Rules

狀態：MVR，OS 案例未驗證。所有 Tier 必備；桌面與手機依任務重新組合內容。

## 重組判斷

- 先保留主要資訊與行動；次要裝飾可簡化，不丟必要內容或功能。
- 依內容決定 Navigation collapse、Grid collapse、Section 順序、字級／行長、間距；不能只把 row 改成 column。
- 圖片在各裝置維持有意義裁切與焦點；文字不依賴圖片中小字。
- Touch targets、表單、對話框、後台資料可操作；Hover 不提供獨有資訊。
- 長標題、錯誤、空列表、較多服務與內容更新狀態也要檢查，不只看預設 Hero。
- 有意義的表格／圖表局部捲動可用，但需事前列於契約並可理解；不能把整頁溢出當成例外。

## 驗證

375／768／1280px 作 v1 共同檢查點；Breakpoint 是實作選擇，檢查點不是必須硬寫的 Breakpoint。檢查 DOM Overflow、文字、導覽、表單、Dialog、圖片及鍵盤／觸控；保存每個主要畫面與重要狀態證據。

Touch target 依 [accessibility](accessibility.md) 的適用標準與例外；不要把 AAA 44px 誤述為 AA 必須值。契約、例外及證據由 [quality](quality.md) 管理。
