# Accessibility｜Minimum Viable Rules

狀態：MVR，OS 案例未驗證。共同基準不代表完整 WCAG 認證；符合等級與適用範圍由契約明列。

## 實作原則

- 優先語意 HTML、合理 Heading／Landmark、正確按鈕／連結／欄位；必要才補 ARIA。
- 表單有可辨識 Label／說明；Error 與 Success 可理解，必要時用適當 live region，不能只靠顏色。
- Keyboard 能完成主要操作；Focus 可見、不被固定元件遮擋，複合元件的焦點進出及返回合理。
- 檢查文字、圖示、邊界的適用 Contrast；重要圖片有文字替代，裝飾圖片不重複朗讀。
- Reduced Motion 降低非必要移動；音訊／影片依需求提供控制與文字替代。
- 觸控尺寸依標準與例外：WCAG 2.2 AA 2.5.8 一般至少 24×24 CSS px；44×44 為 AAA 2.5.5 的增強門檻。專案可設定更大的易用性目標。

## 人工與自動分開

axe 掃描記錄工具版本、頁面與狀態；Violation 與需人工判斷項目分開處理。人工另查鍵盤、焦點、閱讀／Heading 順序、Label／Error、Contrast、圖片與螢幕閱讀器基本理解。不以零 axe findings 宣稱全站合規。

Pass Condition／Evidence／Exception 使用 [quality](quality.md) 的對應要求；不適用要有證據與理由，不能以功能較簡單免除可及性基準。

來源：[WCAG 2.2](https://www.w3.org/TR/WCAG22/)、[2.5.8](https://www.w3.org/TR/WCAG22/#target-size-minimum)、[2.5.5](https://www.w3.org/TR/WCAG22/#target-size-enhanced)、[MDN Reduced Motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)。採用時確認最新適用標準。
