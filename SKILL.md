---
name: website-os
description: Plan, build, critique, verify, and hand off client websites as a Website Product Architect. Use for new websites, substantial redesigns, website product configuration, or website delivery; resume an approved blueprint for scoped updates.
metadata:
  version: "0.1.1"
  architecture: frozen-v1
  maturity: minimum-viable-references
---

# Website OS

Website Professional Operating System，建立在目前 Harness 上。專業角色為 Website Product Architect；同一 Harness 切換責任，不預設固定 Agent 團隊。套件版本由上述 metadata 管理；Architecture Freeze 不代表 v1.0.0 驗收通過。

## 啟動與輸入

沿用宿主 AGENTS／PROJECT_STATE 啟動規則，定位案例目錄與目前有效 Blueprint。輸入為客戶原話、來源／素材、限制、既有系統、授權及目前證據。缺少資料以 Unknown 保存；先查可發現事實，再問會改變方向的問題。

新案執行下列流程；例行修改從核准 Blueprint 回到受影響階段。網站外的公司治理、法律定案、定價與帳號權限繼續由原 authority 負責。

## 流程、產物與完成條件

| 階段／責任 | 載入／產物 | 階段完成條件 |
|---|---|---|
| Discovery | [Discovery 模板](templates/DISCOVERY.md) | 會改變方向的事實、限制、決策者、缺口有來源；詢問高資訊問題 |
| Diagnosis | Discovery 的固定分析維度 | 每個主要判斷可追溯；假設明列；不混入推薦 |
| Recommendation | Discovery 的完整配置方案 | 正式方案逐案明列 Tier、Design Profile、Content Scope、Feature Modules、Operation Plan、Build Path、Scope／Acceptance、取捨／素材／依賴／風險／費用／時程影響 |
| Human Gate | Discovery 決策歷史 | 人類確認方向、Tier、內容／功能／營運／平台、Scope、驗收及重要價值取捨；沿用既有授權 |
| Product Configuration／Planning | [Blueprint 模板](templates/WEBSITE_BLUEPRINT.md) | 核准配置、IA、流程、資料、依賴、排除項與品質契約可執行 |
| Capability Routing | [Capability Matrix](references/capabilities.md) | 能力必要性、最小工具組、Fallback、相容性及載入理由已記錄 |
| Build | 核准 Blueprint／DESIGN 與相關 Reference | 按契約建置；關鍵未知不靠自行假設填補 |
| Critic | [品質規則：方向檢查](references/quality.md#critic) | 核准產品方向、內容、品牌與模板感有具體檢查結果 |
| Verification | [Verification 模板](templates/VERIFICATION.md)、quality | 適用要求有執行結果與可追溯證據；Failed／Blocked 明列 |
| Deployment／Handoff／Maintenance Planning | [部署 Reference](references/deployment.md)、已選 Build Path | 發布依授權；持久性、通知、恢復、責任及移交有實際證據 |

## 契約與狀態

- 資訊不足時先完成 Discovery／有限 Diagnosis。若提供早期暫擬方向，明示尚不是完整 Recommendation；正式比較使用 Discovery 配置表，不能省略 Profile、Content Scope、Operation Plan 或 Build Path。尚未可決定的欄位記 Unknown／依賴及影響，不以省略欄位代替。
- Discovery 保存探索與未核准方案；Blueprint 是唯一有效 Build Runtime Contract。
- Blueprint 不保存未核准 Agent Recommendation；核准後轉為 Owner Decision／Requirement。阻礙工作的 Unknown 先解決。
- 每案 DESIGN 保存具體核准視覺值，Blueprint 引用該檔及版本；[design](references/design.md) 只保存共用方法。
- Scope、功能、平台、費用、時程、驗收的變更先形成 Change Recommendation → Human Gate → 更新 Blueprint。核准範圍內的技術細節由 Agent 處理。
- Critic 可指出問題及建議，不能推翻已核准產品／商業決策；需改決策時回到同一 Human Gate。
- PROJECT_STATE 保存目前工作與下一步；Verification 保存實測結果。套件不另建平行狀態檔。

## 按需載入

這是八份 Professional References + Capability Matrix，另有 Build Path profile。Quality Baseline 對所有網站成立，詳細知識依階段載入：

| 條件 | Professional Reference |
|---|---|
| 要轉譯品牌、組合頁面或檢查視覺 | [design](references/design.md)；新站／重大改版依適用專案規則使用 web-design-selector，例行修改沿用既有 DESIGN |
| 存在動態需求、節奏或效果取捨 | [motion](references/motion.md) |
| 表單、非同步、導覽、複合元件或互動不一致 | [interaction](references/interaction.md) |
| 決定不同裝置上的優先序、重排與輸入 | [responsive](references/responsive.md) |
| 內容不成熟、需要敘事／信任／轉換策略 | [content](references/content.md) |
| 設計／實作可及性行為或人工驗收 | [accessibility](references/accessibility.md) |
| 規劃 Acceptance、Critic、實測、安全／個資／SEO | [quality](references/quality.md) |
| 選擇／操作發布、資料流、恢復、營運責任 | [deployment](references/deployment.md)，並只讀已選路徑 |

先用 quality 的適用清單建立最低契約，按案件深度載入其他模組；不為 Tier 預設載入全部 Reference 或安裝全部工具。

## 驗證、版本與接續

產物必須能區分已核准、已建置、已驗證。文件存在、SMTP accepted、備份檔存在、工具退出成功，各自只能支持相應主張。

OS 0.x 可以迭代。每次實質修正記錄版本、原因、影響能力、案例及 Regression Requirement；版本決策引用案例 Verification。Case B 可使用修正版。最終兩案都通過同一凍結 v1.0.0；舊證據只有在附上仍適用理由時可沿用。

Case A／B 比較資訊架構、Design Profile、User Flow、功能／互動及 Content Strategy（層級、信任、轉換敘事、CTA、Proof）；差異需由需求支持。

接續只讀本 Skill、PROJECT_STATE、有效 Blueprint 及本次相關 Evidence。Discovery 尚未完成時改讀該案 Discovery 與待決問題，不捏造核准 Blueprint。

失敗時先分類為資訊／授權缺口、工具／環境、實作、契約偏離或證據不足；停止依賴該失敗的步驟，保存可重現結果並調整。發現系統缺口修回相關 Reference／Routing／模板，避免僅以臨時 Prompt 繞過。
