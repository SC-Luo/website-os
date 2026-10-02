# Deployment／Handoff｜Minimum Viable Rules

狀態：MVR；未有 Website OS 案例雲端、實際 Email、還原或移交證據。已選 Build Path 另有環境方法，本檔保持平台中立。

## 發布前

1. 核對有效 Blueprint、適用品質／Security／Privacy／SEO Contract、Critic 結果與授權。列出待發布版本、目的地、成本、資料、帳號與回復方式；既有授權沿用，新增影響回 Human Gate。
2. 選環境與秘密注入方式，確認正式 Debug 關閉、Log 最小化、HTTPS、適用 Cookie／Origin／CSRF；具體驗收引用 [quality S01–S10](quality.md)。
3. 核對第三方資料流：來源→接收服務→欄位→用途→保存／存取→Owner；只開核准服務，不將不適用功能預設啟用。
4. 有持久資料時確認可用儲存、應用重啟、版本固定與環境變數；不把 running SQLite 放同步硬碟做多機共用。
5. 確認合成案例 noindex 及正式索引配置的驗證範圍。Privacy Notice 與真實資料用途未知時停止相關資料處理。

## Ownership 與 Operation Plan

Blueprint 的 Ownership Matrix 是核准責任配置 authority；欄位由 [Blueprint 模板](../templates/WEBSITE_BLUEPRINT.md) 定義。Access／Credential Responsibility 記誰管理、授權／撤銷／恢復及私有保管位置的引用，不保存密碼。

Self-managed：可建議客戶日常操作，工作室完成建置／交接；Maintenance：可建議由工作室維護核准技術範圍；Growth：再加核准內容／分析／優化工作。這些是方案建議，不能自動確定任何資產 Owner、SLA、續費或商業責任。每案透過 Human Gate 決定。

實際移交狀態只在 Verification 按資產 ID 保存 Pending／Verified／Blocked／Not applicable、Evidence／接收人／日期。Handoff 引用 Blueprint 配置與實際結果，不複製第三份責任表；PROJECT_STATE 只記交接進度與下一步。

## Delivery 驗收要求

以下 O 項同樣使用 Requirement／Verification Method／Pass Condition／Evidence／Exception Handling。N/A 要證明不適用；必要未知／失敗阻擋交付。

| ID／Requirement | Verification Method | Pass Condition | Evidence | Exception Handling |
|---|---|---|---|---|
| O01 Deploy／HTTPS | 讀真實 URL／TLS／版本，跑適用公開與管理流程 | 核准目的地、版本、設定正確；流程可用 | URL、部署／版本與結果 | 失敗先修正，不公開未核准配置 |
| O02 Persistence | 合成資料寫入→程序重啟／部署→readback | 核准持久資料與關聯不丟失 | 版本、步驟與核對 | 靜態站可 N/A；不可拿本機歷史證據代替 |
| O03 Email | 授權收件帳號實際投遞；故障／未知完成狀態另查 | 達到核准通知／投遞主張，失敗可辨識與受控恢復 | 遮蔽 provider／收件證據／故障結果 | SMTP accepted 不等於收件；缺帳號為 Blocked |
| O04 Backup／Restore | 一致性備份含 DB／必要資產→隔離環境還原→核對 | 可實際恢復需要的資料、關聯及操作；符合案例恢復目標 | 備份版本、還原紀錄、核對與工時 | 不覆蓋原資料；沒有測試資源則 Blocked |
| O05 Rollback | 固定來源／映像版本切換，核對資料相容性及關鍵流程 | 可回到指定可用程式版本且資料仍可用 | 發行識別、前後版本、流程 | 程式回退不等於 DB 還原；破壞性遷移另 Gate |
| O06 Ownership／Access | 按資產 ID 接收確認、授權存取／撤銷／恢復檢查 | 必要資產 Owner／Maintainer／Access 責任已核准且實際移交成立 | Matrix 引用、驗證／接收紀錄 | 未決為 Unknown／Blocked，不用方案名填人名 |
| O07 Operations／Incident | 執行日常更新、監測／故障聯絡與責任 readback | 操作與事件聯絡符合 Operation Plan；限制／費用／續費責任清楚 | 操作紀錄、Owner readback | 不捏造 SLA；必要責任未決則 Blocked |
| O08 Handoff | 接收者依核准指引完成主要管理／恢復任務 | 指引可用，來源／版本／資料／帳號／維護邊界可追溯 | 引用及實際操作／UAT | 沒有接收驗證不能宣稱 Verified |

Backup 保留策略、恢復目標、Email provider、帳號 Owner 由案例決定，不在本檔硬寫。必要秘密及資料不貼到公開文件或聊天。
