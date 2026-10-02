# Quality｜Verification Contract 與 Critic

狀態：Minimum Viable Reference 0.1.0；契約已定義，Website OS Case A／B 尚未執行。規則存在不等於 Passed。

## 契約格式與使用

Blueprint 在 Build 前指定主要頁面／重要狀態／User Flow、適用要求、案例目標及例外。下表是共用要求 authority；案例引用 ID，只保存該案的適用範圍及目標，不複製另一份規則。

每項使用 Requirement → Verification Method → Pass Condition → Evidence → Exception Handling。Evidence 應有日期、OS／應用／Blueprint 版本、範圍、工具／環境、實際結果與可開啟位置；不得含秘密或不必要個資。

結果：Passed／Failed／Not run／Blocked／Not applicable。後者需證明功能／情境不存在；Unavailable 不是 Not applicable。Exception 記錄理由、影響、替代驗證、責任者、核准及處置，不把例外改成 Passed。

X：共同 Exception Handling。必要要求 Failed／Blocked 或結果未執行，阻擋相應交付／Freeze；先修正再回歸。未核准例外不能自動免除基準。自動化結果與人工結果分開。

## 共同品質要求

| ID／Requirement | Verification Method | Pass Condition | Evidence | Exception Handling |
|---|---|---|---|---|
| Q01 Responsive | 375／768／1280px 檢查 DOM、截圖、主要畫面及錯誤／展開狀態 | 無非預期橫向 Overflow、遮擋或不可達操作 | 各尺寸／狀態結果及截圖 | X；局部必要捲動需契約指定且可操作 |
| Q02 Keyboard／Focus | 僅鍵盤執行主要流程，檢查順序、Dialog／返回與可見焦點 | 主要操作可完成、無陷阱、Focus 可見且不被遮擋 | 流程／焦點紀錄 | X |
| Q03 Reduced Motion | 模擬 prefers-reduced-motion，比較一般設定 | 非必要移動降低或停用，內容／必要回饋仍可用 | 設定與結果 | X；無動態也需實際檢查 |
| Q04 axe | 對主要頁面與重要狀態執行適用掃描 | 適用違規已修正；incomplete／人工項目完成分類與另查 | 工具版本、報告、處理紀錄 | X；無法執行為 Blocked |
| Q05 Manual Accessibility | 另查語意、Label／Error、閱讀順序、Contrast、圖片、螢幕閱讀器基本理解 | 達成 Blueprint 指定範圍／等級，無未解必要缺陷 | 人工清單與操作結果 | X；零 axe 不代替本項 |
| Q06 Browser | Chromium＋WebKit 跑關鍵流程；Safari 特有依賴補實際 Safari | 核准流程在兩引擎正確，特有行為已查證 | 瀏覽器版本、流程結果 | X；差異要列 Known issue |
| Q07 Form／Retry | 成功、無效輸入、伺服器／網路失敗與重試 | success／error／retry 可辨識，輸入合理保留；重試不產生非預期重複 | 請求／狀態／資料核對 | X；無表單可證明 N/A |
| Q08 Performance | Lighthouse；保存 URL、工具、裝置／節流、執行環境／日期，對照預定目標 | 符合 Blueprint 事先定義且可量測的目標 | 報告、目標比較、限制 | X；缺目標／測量不宣稱通過 |
| Q09 Images／Assets | 查格式、尺寸／DPR、體積、載入、裁切、替代文字與授權 | 符合案例事先指定尺寸／體積／畫質預算；非首屏合理延後，避免布局跳動 | 資產清單、大小與視覺結果 | X；不存在資產需說明 |
| Q10 Content／Links | 對核准文字、來源、CTA、連結與主要行動 readback | 內容正確，無捏造證據／承諾，主要行動可用 | 核准來源、頁面／連結結果 | X |
| Q11 Visual consistency | 截圖對照 DESIGN 檢查字型、色彩、Spacing、裁切、折行、元件 | 具體視覺值與核准 DESIGN 一致，無必要畫面缺陷 | 截圖及差異結果 | X；方向適合性另經 Critic |

Lighthouse 的實驗室結果不宣稱為真實流量效能；沒有 field data 就明列 unknown。CWV 起始參考為 p75 LCP≤2.5s、INP≤200ms、CLS≤0.1，採用時查核最新官方資料與量測來源，不拿單機報告代替 field data。

## Security／Privacy Baseline

只執行實際適用項目；不為靜態站新增登入。quality 定義要求，deployment 定義部署與營運執行方法。這是共同最低檢查，不是完整資安或法律合規認證。

| ID／Requirement | Verification Method | Pass Condition | Evidence | Exception Handling |
|---|---|---|---|---|
| S01 Input Validation | 正常／異常型別、長度、允許值及業務語意請求；核對資料 | 伺服器拒絕無效輸入，無不當寫入；前端不作唯一保護 | 請求／回應及資料核對 | X；無輸入需列適用理由 |
| S02 Output Escaping | 不可信文字於公開、後台、適用 Email 輸出測試 | 按輸出情境編碼／安全處理，內容不執行注入 | 合成測試內容與輸出 | X；不得只靠 S01 判定 |
| S03 Authentication／Authorization | 有效／無效登入、未登入／越權／跨案私有讀寫 | 身分及每項私有操作授權正確，拒絕無授權操作 | 授權測試與資源核對 | X；無登入不能免除存在的私有授權 |
| S04 Session／Cookie／CSRF | 檢查 Cookie、過期／登出、適用 CSRF 攻擊請求 | 正式 Cookie 有適用 Secure／HttpOnly／SameSite；失效後不可用；適用偽造請求被拒 | 遮蔽設定／請求結果 | X；依認證模式判斷適用性 |
| S05 Secrets | 檢查公開資產／設定／回應、repo 改動及錯誤輸出 | 不暴露 Secret／憑證／私有路徑；秘密保存在核准私有位置 | 無秘密的檢查紀錄 | X；不得貼秘密作證據 |
| S06 Debug／Logs | 正式模式觸發合成錯誤與成功事件，查回應／Log | Debug 關閉，無堆疊／秘密／不必要敏感輸入；必要事件可辨識 | 遮蔽的回應與 Log 檢查 | X |
| S07 Data minimization | 核對欄位與收集用途、第三方傳送 | 每項收集有用途及最少必要資料，無多餘敏感欄位 | 欄位／用途對照 | X；不自行添加行銷資料 |
| S08 Retention responsibility | 核對保存期限、存取／刪除／備份責任及操作方法 | 適用責任與期限經 Owner 決定，可按契約執行 | 核准要求、操作／責任引用 | X；未知不得假定無限保存 |
| S09 Privacy Notice | 核對收集點告知與實際資料流、核准版本 | 適用告知可取得且一致，Owner 已核准，需專業審閱項目已處理 | 告知／核准／資料流引用 | X；不以 Agent 文案宣稱法律合規 |
| S10 Third-party data flow | 核對 Email／Analytics／API 等服務、用途、資料、存取與責任 | 真實資料流與核准配置一致，責任已決定 | 服務／流向與 Ownership 引用 | X；未選配功能不預設開啟 |

需要真實資料而 S07–S10 關鍵責任／告知未知時，先 Human Gate；合成測試通過不代表真實資料合規。

## Technical SEO Foundation

驗證網站可控制的技術基礎，不承諾排名、流量、成交、實際收錄或搜尋呈現。每個環境先指定 index／noindex；合成案例預設 noindex。robots／noindex 不代替 S03 私有資料保護。

| ID／Requirement | Verification Method | Pass Condition | Evidence | Exception Handling |
|---|---|---|---|---|
| T01 Page Title | 讀主要公開頁 HTML，對照頁面清單 | 適用頁標題存在並對應目的，無誤用 | URL／title 對照 | X |
| T02 Meta Description | 讀 HTML 與核准內容 | 適用頁 description 有意義且對應內容 | URL／description 對照 | X |
| T03 Canonical | 檢查 rel canonical 與核准標準 URL | 格式／位置正確，域名／路徑一致，無意外指向測試或別案 | HTML／URL 對照 | X |
| T04 robots | 讀 robots.txt、meta／X-Robots-Tag | 與環境及頁面索引策略一致，正式頁無意外全站封鎖 | 設定／HTTP 回應 | X；robots 禁爬不等同保證不索引 |
| T05 sitemap | 讀 XML，逐項查核准 URL | 適用清單可讀、URL 有效且符合 canonical，不含後台／私有／失效頁 | sitemap／URL 結果 | X；合理 N/A 需事先列明 |
| T06 Semantic Headings | 查 DOM 與人工閱讀順序 | 標題反映核准內容層級，不靠字型尺寸偽裝語意 | DOM／人工結果 | X |
| T07 Open Graph | 查 metadata、URL 與圖片回應 | 適用分享資料正確，資產可讀且非私有 | HTML／資產結果 | X |
| T08 Indexability | HTTP、可取得 HTML、認證、redirect 及 robots 指令一起查 | 與核准 index／noindex 策略一致；測試保護與正式配置另驗 | 環境／頁面結果 | X；不以搜索是否收錄作 Pass |
| T09 404 | 請求不存在公開頁 | 真正 HTTP 404，提供合理返回，不誤回 200 假頁 | HTTP／畫面 | X |
| T10 Internal Linking | 檢查主要導覽、CTA、內容連結／錨點 | 指向正確且可達，無非預期斷鏈 | 連結結果 | X |
| T11 Structured Data | 僅適用類型查 JSON-LD／對應驗證與可見內容 | 語法／必要欄位正確，內容真實且一致 | 驗證結果／N/A 理由 | X；不為驗收硬加類型 |

未設定／未執行的項目不能泛稱 SEO Passed。

## Critic

Critic 回答產品方向是否仍成立；Verification 回答功能與品質是否實際完成。先看核准 Blueprint、DESIGN、需求及現有畫面，避免只看 Executor 自評。

固定檢查：Blueprint adherence、Design Profile consistency、Visual hierarchy、Brand consistency、Content hierarchy、Content Strategy、Motion appropriateness、Interaction consistency、跨 Section 一致性、Generic-template check。

Generic-template：遮去 Logo／品牌文字／圖片／主色，檢查 IA、敘事、流程與 Pattern Composition 是否仍由這個受眾與商業目的導出。與另一案例高度相同時提供具體位置及理由，回到 Profile／IA／Content／Composition 檢討；共用原生元件本身不等於罐頭網站。

Critic findings 保存：觀察、核准依據、影響、修正建議、是否需 Change／Human Gate、處理與再查結果。不能自行修改已核准 Tier、方向、Content Scope、功能、營運、平台、Scope 或商業決策。跨核准決策的修正形成 Change Recommendation，核准及更新 Blueprint 後才執行。自動化工具通過不能抵銷重大方向偏離。

## Acceptance Questions / Evidence Rubric

這是原 12 題正式驗收問題與證據規則，不是平均分數。

| 題 | 問題與所需 Evidence | 性質 |
|---|---|---|
| 1 | 模糊需求時查／問真正會改變方向的資料；Discovery／來源及問題結果 | Evidence Completeness |
| 2 | 客戶語言轉為可追溯 Business／Brand／Content／Functional Diagnosis | Evidence Completeness |
| 3 | 提出實質不同完整 Product Configurations；方案比較與取捨 | Evidence Completeness |
| 4 | Recommendation 與 Human Decision 分開，核准後形成有效 Blueprint | Gate＋Evidence Completeness |
| 5 | 最少且適合的 Reference／Skill／Library／Tool；Routing 理由 | Evidence Completeness |
| 6 | 基準與選配明確，適用必要要求通過 | Gate |
| 7 | 不載入全部 Reference 也能工作；實際使用紀錄 | Evidence Completeness |
| 8 | Critic 檢查方向，Verification 支持實際品質 | Gate＋Evidence Completeness |
| 9 | 同 OS 的 A／B IA／Profile／Flow／功能／Content Strategy 有可追溯差異 | Gate＋Evidence Completeness |
| 10 | 新 context 僅依 Skill／PROJECT_STATE／Blueprint／相關 Evidence 成功接續 | Gate＋Evidence Completeness |
| 11 | OS 修改能辨識案例 Regression，需查項目已執行／舊證據適用理由成立 | Gate＋Evidence Completeness |
| 12 | 發布清單有已驗證／未驗證能力、限制、Build Paths、風險與下一步 | Evidence Completeness；缺必要披露阻擋發布 |

Freeze 需適用 Gate 成立、必要 Failed／Blocked 已處理、Evidence 足以支持結論；其他通過項目不能平均抵銷。必要交接要求由 [deployment](deployment.md) 指定，納入案例驗收。現階段所有案例 Rubric 為 Not run。

## 來源與採用邊界

原始來源為 Owner 指定「網頁精美元素建議」及本次 Website OS 計畫；具體 Contract 是 Owner 核准的內部驗證規格。

- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)、[CWV thresholds](https://web.dev/articles/defining-core-web-vitals-thresholds)。
- [OWASP Input Validation](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)、[XSS](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)、[Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)、[Session](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)、[CSRF](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)。
- [Google SEO Starter](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)、[canonical](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)、[noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing)。

來源標準／工具在實際使用時再確認版本；本契約不是外部供應商保證、法律意見或完整安全認證。
