# Website OS

**Website Professional Operating System · Website Product Architect**

讓 AI Agent 從理解客戶需求、提出完整網站方案，到建置、設計檢查、品質驗證與營運交接，都有可追溯的工作方法。

分享入口：[SC-Luo/website-os](https://github.com/SC-Luo/website-os)。主要文件以繁體中文撰寫。

## 目前版本與範圍

- 主 Skill 版本：**0.1.1**，Minimum Viable References。
- v1 的架構分工已暫時凍結；完整 **v1.0.0 驗收尚未完成**。
- 這份套件提供工作流程、專業規則、能力選型與空白模板；沒有附網站成品、後端程式或客戶資料。
- 原專案已用於 Case A／B 本機建置；本公開套件未包含私有案例的測試報告，不以此宣稱所有能力已驗證、正式上線或完成交付。
- Reference 的初始 `Not run`／未驗證標記不代替任何使用者的案例結果；能力支援必須由該案實際版本、範圍與 Evidence 支持。
- 雲端部署、真實 Email 投遞、完整營運交接與跨 context 最終驗收仍有未驗證範圍。新增 Build Path 需另有案例證據。

## 它如何工作

Website OS 建立在你既有的 Agent Harness 上。Harness 提供上下文、工具、執行環境與權限；Website OS 提供網站專業責任與判斷方法。

同一 Harness 依階段切換責任，沒有固定多 Agent 團隊。

```text
Discovery → Diagnosis → Recommendation
→ Human Gate → Product Configuration → Blueprint
→ Capability Routing → Build → Critic → Verification
→ Deployment → Handoff → Maintenance Planning
```

1. **理解需求**：先查可取得的資料，再詢問真正會改變方向的問題。
2. **形成判斷**：從 Business、Audience、Brand、Content、功能與營運等固定維度分析，主要判斷都有來源。
3. **提出完整方案**：比較 Tier、Design Profile、Content Scope、Feature Modules、Operation Plan、Build Path、範圍及取捨。
4. **保留人類決策**：方向、商業承諾、費用、平台與重要範圍由 Owner／Client 核准。
5. **按契約建置**：只有核准內容進入有效 Blueprint，按需載入最少且適合的規則與工具。
6. **分開檢查方向與結果**：Critic 檢查品牌、內容與體驗；Verification 用實際 Evidence 判定功能與品質。
7. **交接營運責任**：確認資產所有權、維護、帳號責任、備份還原、回退與接收結果。

## 套件內容

入口是 [SKILL.md](SKILL.md)。架構為 **一個主 Skill + 八份 Professional References + Capability Matrix**，Build Path 獨立管理。

```text
website-os/
├── SKILL.md
├── README.md
├── references/
│   ├── design.md
│   ├── motion.md
│   ├── interaction.md
│   ├── responsive.md
│   ├── content.md
│   ├── accessibility.md
│   ├── quality.md
│   ├── deployment.md
│   ├── capabilities.md
│   └── build-paths/
│       └── node-sqlite-render.md
└── templates/
    ├── DISCOVERY.md
    ├── WEBSITE_BLUEPRINT.md
    └── VERIFICATION.md
```

| 文件 | 使用時機 |
|---|---|
| [design](references/design.md) | 品牌轉譯、視覺層級與 Composition；保存 How to design |
| [motion](references/motion.md) | 動態目的、工具取捨、Reduced Motion 與效能 |
| [interaction](references/interaction.md) | 表單、導覽、操作狀態、錯誤與重試 |
| [responsive](references/responsive.md) | 各裝置的資訊優先序、重排及觸控 |
| [content](references/content.md) | 敘事、信任、Proof、CTA 與內容工作範圍 |
| [accessibility](references/accessibility.md) | 語意、鍵盤、焦點與人工／自動檢查 |
| [quality](references/quality.md) | 品質／Security／Privacy／Technical SEO Contract、Critic 與驗收問題 |
| [deployment](references/deployment.md) | 發布、持久性、恢復、Ownership 與交接 |
| [Capability Matrix](references/capabilities.md) | 依需求選型、Fallback、相容性、風險與驗證 |

[Node＋SQLite＋Render](references/build-paths/node-sqlite-render.md) 是候選 Reference Build Path v1，不是 Website OS 的必要技術棧。文件中的歷史工具版本與原型限制需在實際採用時重新確認；原型程式沒有隨本套件提供。

## 開始使用

### 1. 取得套件

下載 GitHub ZIP，或在你選定的工作目錄中執行：

```sh
git clone https://github.com/SC-Luo/website-os.git
```

GitHub 倉庫根目錄即為完整 Skill 目錄。若你的 Agent 支援本地 Skill，將整個資料夾放入它支援的 Skill 位置，保留 `SKILL.md`、`references/`、`templates/` 的相對結構。已有同名 Skill 時先比較與保留原版本。

本套件是 Markdown，沒有安裝腳本、套件安裝或自動部署。請先開啟 `SKILL.md`；Agent 不支援自動發現 Skill 時，可明確提供該檔及必要 Reference。

### 2. 在你的網站專案開始 Discovery

沿用專案的 `AGENTS.md` 與 `PROJECT_STATE.md`；沒有既有狀態文件時，在網站專案建立一份最小 `PROJECT_STATE.md`，記錄目標、目前階段、已知／未知、待決事項與下一步。這是使用者專案的狀態，不是此套件的另一份規格。

從 [Discovery 模板](templates/DISCOVERY.md) 建立該案 `DISCOVERY.md`。先保留客戶原話與資料來源，未知保持 Unknown。

可以把以下需求交給 Agent：

> 請使用 website-os，為我的網站專案開始 Discovery。先讀專案的規則與目前狀態，整理既有事實及真正影響方向的缺口，再提出少量高資訊問題。接著形成可追溯 Diagnosis，提出 2–3 個有實質差異的完整 Website Product Configuration；方向經我核准後，再建立有效 Blueprint。

### 3. 核准後才建立 Build Contract

使用 [Blueprint 模板](templates/WEBSITE_BLUEPRINT.md) 保存核准配置與驗收要求。每案 `DESIGN.md` 保存該站已核准的具體視覺決策；Blueprint 引用它，不重複保存字型、色彩等設定。

使用 [Verification 模板](templates/VERIFICATION.md) 保存實際結果。未執行項目是 `Not run`；適用性、例外與限制逐項記錄，不把文件存在視為通過。

| 產物 | 唯一責任 |
|---|---|
| `DISCOVERY.md` | 來源、Diagnosis、方案、取捨與決策歷史 |
| `WEBSITE_BLUEPRINT.md` | 現在正式要做什麼；唯一有效 Build Runtime Contract |
| 每案 `DESIGN.md` | 該站已核准的視覺配置 |
| `VERIFICATION.md` | Critic findings、測試、回歸、移交及實際 Evidence |
| `PROJECT_STATE.md` | 當前階段、阻礙、待決與下一步 |

## 維持的產品原則

- Essential／Brand／Experience 是策略與製作深度，全部保有共同品質基準。
- Design Profile、Feature Modules、Content Scope 與 Build Path 各自配置，不綁死 Tier。
- Experience 不以動畫數量判斷；不同案例需由需求推導 IA、內容策略、流程與設計。
- 不預先安裝大量 Library，不把工具名稱當能力，不自動把 Reference 拆成 Skill。
- Critic 不能覆寫已核准商業決策；影響配置／Scope 的修正回同一 Human Gate。
- Security／Privacy 與 Technical SEO 先判斷適用性，再按 Requirement／Method／Pass Condition／Evidence／Exception 執行。
- 驗收問題包含 Gate 與 Evidence Completeness，不平均計分；必要 Failed／Blocked 不能被其他通過項抵銷。

## 工具與宿主責任

檔案、瀏覽器、執行環境與第三方帳號由宿主提供。shadcn、Radix、Motion、Playwright、axe、Lighthouse 等都是按需選擇的工具，本倉庫沒有安裝或宣稱全部支援它們。

`web-design-selector` 僅在宿主專案規則要求時使用；本套件沒有綁定該 Skill 或私有設計庫。外部技能與上游工具各自的使用條件需另行確認。

## 修正與分享

改進優先來自案例 Evidence。修改規則時記錄原因、版本、影響能力、案例與定向 Regression；只沿用仍可支持結論的舊證據。Architecture Freeze 不阻止 0.x 的案例驅動修正。

此倉庫為主套件的公開發行快照；客戶專案、私人決策歷史、帳號、密碼、資料庫與內部 Evidence 保存在各自專案。公開 Issue／Pull Request 請只提供已去識別化的必要資訊。

授權狀態：本次分享尚未指定 `LICENSE`，也未選定 MIT 或其他開源授權。
