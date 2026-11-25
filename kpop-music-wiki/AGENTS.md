# AGENTS.md — K-Pop 音樂特徵與熱門歌曲預測 LLM Wiki 憲法 (Schema)

## 1. 專案願景與執行環境
- **主題**：K-Pop 音樂特徵、曲風結構與熱門歌曲預測（Hit Song Science & Structural Evolution）。
- **語言規範**：所有 Wiki 頁面以**繁體中文**撰寫，核心音樂資訊檢索（MIR）與學術專有名詞（如 `BPM`、`Danceability`、`Energy`、`Valence`、`SMP`、`Hook`、`Hit Song Science`、`Multimodal`）保留英文並附簡短中文解釋。
- **執行環境**：本倉庫託管於 GitHub，並可搭配 VS Code（GitHub Copilot / Claude Code / Codex）與 GitHub Pages（發布教學 HTML 簡報）運作。

## 2. 三層架構規範 (Three-Layer Architecture)
1. **`raw/`（原始資料層 — 唯讀 Source of Truth）**：
   - 存放至少 5 篇核心學術論文的 PDF、BibTeX 或純文字摘要（建議命名：`01-author-year-keyword.pdf` 或 `.md`）。
   - **鐵律**：LLM 只能讀取 `raw/`，嚴禁修改或刪除原始論文檔案。
2. **`wiki/`（知識庫層 — LLM 全權維護）**：
   - `wiki/index.md`：內容導向總目錄（依論文、概念、比較頁分類），每次 `ingest` 必更新。
   - `wiki/log.md`：時間軸日誌（Append-only），格式嚴格遵守 `## [YYYY-MM-DD] <operation> | <title>`。
   - `wiki/overview.md`：全局演進總覽（作為最終製作教學 HTML 簡報的主幹）。
   - `wiki/papers/`：單篇論文深度解析頁。
   - `wiki/concepts/`：跨論文提煉的音樂特徵與結構概念頁（如 `hook-theory.md`、`tiktok-effect.md`）。
   - `wiki/comparisons/`：跨論文觀點衝突、數據差異與榜單對比頁（如 `melon-vs-spotify.md`）。
3. **`slides/`（教學成果層 — HTML 簡報）**：
   - 存放基於 `wiki/` 內容生成的自包含（Self-contained）互動式教學 HTML 簡報（`slides/index.html`），可直接透過 GitHub Pages 部署瀏覽。

## 3. 標準操作流程 (Operations & Loop)

### A. Ingest 流程（「先討論、後生成」原則）
每當使用者提供一篇新論文（放入 `raw/` 或貼上內容）時，必須依序執行以下迴圈：
1. **Discuss（討論確認）**：先提取論文的核心主張、資料集、關鍵指標與模型結果，與使用者確認「重點切入角度」及「對既有 Wiki 認知的影響」，**未經確認前不直接覆寫核心結論**。
2. **Draft & Integrate（寫入與整合）**：
   - 建立 `wiki/papers/paper-XX-<slug>.md`。
   - 更新或新建相關的 `wiki/concepts/*.md` 與 `wiki/comparisons/*.md`。
   - 更新 `wiki/overview.md` 的演進脈絡。
3. **Bookkeeping（索引與日誌）**：
   - 更新 `wiki/index.md` 條目與連結。
   - 在 `wiki/log.md` 底部追加一筆 `## [YYYY-MM-DD] ingest | <論文標題>` 紀錄。
4. **Verify（一致性檢查）**：檢查所有 Markdown 內部連結（`[標題](../concepts/xxx.md)`）是否有效、數值單位（如秒數、BPM、準確率）是否與 `raw/` 一致、是否標註了與前幾篇論文的「衝突或補充（Delta）」。

### B. Query 與簡報生成流程
- 回答問題或生成 `slides/index.html` 時，**優先讀取 `wiki/index.md` 與 `wiki/overview.md`**，再按需深入 `wiki/papers/` 與 `wiki/concepts/`，嚴禁脫離 Wiki 憑空捏造數據。
- 簡報內容必須能讓「完全不懂音樂資訊檢索（MIR）與 K-Pop 產業分析的初學者」看懂基本概念，並附上論文出處引用。

### C. Lint 健檢流程
- 定期檢查：是否有孤島頁面（Orphan pages，無任何頁面連入）、是否有概念被提及超過 2 次卻尚未建立專屬 `concepts/` 頁面、是否有新舊論文數據矛盾未標註。

## 4. 單篇論文頁面標準模板 (`wiki/papers/paper-XX-*.md`)
```markdown
# [論文編號] 論文中文譯名 (Original English Title)

- **作者與年份**：Author et al. (Year)
- **原始檔案**：`raw/xx-filename`
- **研究資料集**：（例如：Melon Top 100 / Spotify Audio Features / Billboard Hot 100，樣本數 N=...）
- **核心方法/模型**：（例如：Random Forest, XGBoost, Audio Signal Processing, Multimodal CNN）

## 1. 研究問題與背景
## 2. 關鍵音訊/結構特徵指標
## 3. 核心實驗結果與數據
## 4. 與既有知識的衝突或補充 (Delta & Contradictions)
- **支持了什麼**：
- **修正/挑戰了什麼**：
## 5. 相關概念連結
- [概念名稱](../concepts/xxx.md)
```
