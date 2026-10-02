# Capability Matrix｜選型規則

狀態：0.1.0 文件層 MVR；Website OS 案例能力尚未驗證。八份 Professional References + Capability Matrix；Build Path profile 另計，不作第九份 Professional Reference。

## 先判斷，再選工具

根據 Blueprint 的需求／基準決定能力，再考慮 native／既有相容能力／最小新實作。新增 Library／Tool 前寫出現有缺口、案例依據、相容性、成本／風險、Fallback 與驗證；先在案例內試驗，不因市場存在而納入支援。

Support Status：Documented-unverified（規則已寫）、Candidate（已知缺口待試驗）、Implemented-unverified、Verified（限具體版本／路徑／證據）、Unsupported。工具已安裝不能升級為 Verified。

以下初始主表全部 Documented-unverified。歷史 delivery-template evidence 只能支持原版本／scope；要提升 OS 能力需案例契約及新增證據。

| Capability | Quality Baseline | 深度載入條件／Reference | Preferred Implementation | Fallback | Framework Compatibility | Dependencies | Cost／Risk | Verification Method | Support Status |
|---|---|---|---|---|---|---|---|---|---|
| Design | Yes | 品牌／Composition／Critic；[design](design.md) | 核准 DESIGN＋專案設計選擇流程 | 簡化至仍符合 Profile 的 Pattern | 平台中立 | 核准方向／內容／素材 | 客製深度、來源授權、模板感 | DESIGN 對照與 Critic | Documented-unverified |
| Responsive | Yes | 重排／觸控；[responsive](responsive.md) | CSS／既有布局 | 單一可讀可操作的重排 | 各前端 | IA／內容優先序 | 裝置／長內容遗漏 | Q01／Q02／Q06 | Documented-unverified |
| Interaction | 適用基本狀態 Yes | 表單／複合流程；[interaction](interaction.md) | native HTML＋現有模式 | 減少非必要複合元件 | 原生；React 可另評 shadcn／Radix | 流程／資料契約 | 狀態／競態／鍵盤 | Q02／Q07＋功能測試 | Documented-unverified |
| Motion | 必要回饋 Yes；特效 No | 動態有目的；[motion](motion.md) | CSS／原生能力 | 無非必要動畫但保留回饋 | 原生；JS Motion 待必要性；React 候選另查 | 核准 Motion Tone | 效能／Reduced Motion／依賴 | Q03／Q08＋Critic | Documented-unverified |
| Content | 正確可理解 Yes | 未成熟內容／策略；[content](content.md) | 客戶素材＋核准整理 | 簡化內容，顯示真實缺口 | 平台中立 | 事實／Proof／核准 | 捏造、工作量與授權 | Q10＋Content Critic | Documented-unverified |
| Accessibility | Yes | 語意／複合行為／驗收；[accessibility](accessibility.md) | 語意 HTML＋人工／axe | 簡化到可操作原生流程 | 不依賴 UI 框架 | 適用等級／工具可用性 | 自動檢查漏項 | Q02–Q06 | Documented-unverified |
| Security／Privacy | 適用 Yes | 輸入／私有操作／資料流；[quality](quality.md)＋[deployment](deployment.md) | 平台／現有驗證、授權、秘密管理 | 限制資料與功能；缺保護停止相關操作 | 依認證／平台 | 資料與責任核准 | 洩漏／個資／錯誤授權 | S01–S10 | Documented-unverified |
| Technical SEO | 適用 Yes | 環境／公開頁驗收；[quality](quality.md) | 伺服器／靜態輸出 metadata 與正確 HTTP | 簡化公開頁；缺設定標未完成 | 各網站 | 公開 URL／索引策略 | 測試索引／錯 canonical | T01–T11 | Documented-unverified |
| Quality | Yes | Build 前契約／Build 後驗收；[quality](quality.md) | 實測＋截圖＋Critic；Playwright／axe／Lighthouse 按需 | 人工等價驗證若契約允許，否則 Blocked | 對實際頁面／API | 可用環境、帳號、目標 | 假 Passed／工具覆蓋不足 | 契約、Rubric、版本證據 | Documented-unverified |
| Deployment／Ownership | 依交付適用 | 準備發布／交接；[deployment](deployment.md) | 已核准 Build Path／provider 方法 | 延後外部操作，完成可審閱本機成果 | 平台中立路由 | 授權／帳號／責任／成本 | 成本／持久性／資料損失 | O01–O08 | Documented-unverified |

## 功能與 Build Paths

Case A 以內容＋詢問管理驗證；Case B 以單店預約營運驗證，均由實際 Blueprint 配置。Booking、CMS、CRM、Commerce、Membership、LINE、AI、Payment 等名稱只是可能需求；不因列出就實作／承諾支援。

[Node＋SQLite＋Render](build-paths/node-sqlite-render.md) 為 Reference Build Path v1：歷史本機能力見既有 evidence，公開路徑尚未驗證。其他 Next.js／Vercel／Supabase、Static／Cloudflare、CMS、GAS 路徑是未驗證候選，只有案例需要才建立 profile。
