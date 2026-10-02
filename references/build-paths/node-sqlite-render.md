# Reference Build Path v1｜Node＋SQLite＋Render

狀態：Candidate for cloud validation。不是 Website OS runtime 依賴，也不是已驗證雲端交付。歷史方法／規格基礎為內部 delivery-template 0.5.0、schema 2；該原型程式與案例 Evidence 未包含在公開套件。實際採用時以所選實作的 API 契約／操作指引為準，不能假設取得本 Skill 就已有可執行後端。

## 已知起點與限制

- Node engines >=24.16.0 <25；node:sqlite；Nodemailer 10.0.13、Sharp 0.35.5。前端原生 HTML／CSS／JS。
- 內容／詢問／選配能力已有歷史本機證據，各案例程序、DB、憑證獨立。這些不自動成為 OS Case A／B Passed。
- 目前只 bind 127.0.0.1，精確 Host／Origin 及本機 Cookie；不支援公開模式。不能用 tunnel 當正式部署。
- 真實 SMTP、Linux／Sharp、持久 disk、HTTPS 管理身分／Cookie、固定發行與雲端回退未驗證。

## 案例需要時補齊

1. 先核對 Blueprint 與可重用後端邊界；按案例 IA／Content／Profile 建前端，不能沿用原樣板 Hero 就宣稱另一產品。
2. 在隔離案例建置固定 Node／來源或映像，驗證 Linux／原生依賴；明確區分 local／production Host、Origin、HTTPS 與 Secret 設定，不能以關閉保護換公開。
3. 公開 API／HTML、Session／CSRF／Debug／Logs 執行 quality 的 S 要求；公開環境不沿用只供本機展示的弱憑證。
4. Render 使用核准的 web service／持久 disk，確認資源費用與 Owner。SQLite 為單寫入實例，擴展／部署中斷限制必須記錄並符合案例營運目標。
5. 一致性備份 DB＋必要素材，安全異地保管；真實還原至隔離資源核對。Render disk snapshots 不當作自管 DB 還原證據。
6. 真實 Email 只向授權收件者測試；accepted、delivered／received 與故障分開。程式版本回退與 DB／資產還原分開驗證。
7. 依 deployment O01–O08 完成操作、Ownership 與交接；保留程序版本、資料相容性、支出與實際工時。

資料與憑證不放共用公開設定；Running DB 不放 Drive。只有正式來源、文件與無秘密 evidence 保存到專案。

## 官方來源（執行前重新確認）

[Node SQLite](https://nodejs.org/download/release/v24.16.0/docs/api/sqlite.html)、[Render Docker](https://render.com/docs/docker)、[Web services](https://render.com/docs/web-services)、[Disks](https://render.com/docs/disks)、[Rollbacks](https://render.com/docs/rollbacks)、[Pricing](https://render.com/pricing)。不將舊報價／工具版本或本機結果當新雲端事實。
