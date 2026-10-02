# Motion｜Minimum Viable Policy

狀態：MVR，案例未驗證。只在動態需求／取捨出現時深讀；基本回饋也可以透過原生狀態完成。

## 選擇規則

每個動態先寫目的：Hierarchy、Feedback、Continuity、Attention 或 Delight。再決定觸發、作用範圍、時間／Easing、重播、Reduced Motion 與失敗 Fallback。

可用類型：Entrance／Reveal、Exit、Hover、Press、Scroll-triggered、Scroll-linked、Layout、Shared-element、Page Transition；不要求每案全部使用。

時間起始參考：微互動 120–200ms、一般切換 200–350ms、區塊揭露 350–600ms、Hero 600–1000ms、Stagger 間隔 40–100ms。這些來自原討論，是原型參考，不是共同驗收門檻。位移／縮放由內容與裝置調整，不機械套用。

## 實作

先考慮 CSS／原生瀏覽器；需要 JavaScript 協調時先看既有相容能力。[Capability Matrix](capabilities.md) 決定工具。React 路徑可考慮相容的 Motion Primitives／Motion／Magic UI；原生路徑不為效果引入 React。GSAP／Lenis／WebGL 僅在具體案例缺口成立後試驗。

優先 transform／opacity；大型模糊、循環、視差需量測。Scroll-linked 只在敘事必要時選擇；避免攔截捲動或使主要內容等待動畫才可用。

Do：動態短且可預期；保留操作結果；Reduced Motion 降低非必要移動。

Don't：因 Experience 加入更多動畫；用 Hover 作唯一資訊入口；效果失效就隱藏主要內容。

## 驗證

使用一般／Reduced Motion 設定、375／768／1280px、觸控與鍵盤檢查；保存觸發、完成、無動畫 Fallback 及實際效能證據。執行契約見 [quality](quality.md)。

來源：[Apple Motion](https://developer.apple.com/design/human-interface-guidelines/motion)、[MDN Reduced Motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)、[動畫效能](https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/CSS_JavaScript_animation_performance)、[Motion JavaScript](https://motion.dev/docs/quick-start)。工具版本與支援在採用時再查核。
