# K-Pop 音樂特徵與熱門歌曲預測 — LLM Wiki 知識庫

本專案參考 Andrej Karpathy 的 **LLM Wiki** 架構設計，針對「K-Pop 音樂特徵、曲風結構演進與熱門歌曲預測（Hit Song Science）」領域建立可持續累積的個人知識庫，並以此為單一事實來源（Single Source of Truth）生成教學型 HTML 簡報。

## 資料夾結構

```text
kpop-music-wiki/
├── AGENTS.md                 # LLM Wiki 核心規範與工作流 Schema
├── README.md                 # 專案說明與 GitHub 工作流指南
├── .github/workflows/        # GitHub Pages 自動部署教學簡報設定
├── raw/                      # 原始論文資料（唯讀，至少收錄 5 篇論文）
├── wiki/                     # LLM 維護的結構化知識庫
│   ├── index.md              # 知識庫總目錄
│   ├── log.md                # 知識庫演進日誌
│   ├── overview.md           # K-Pop 熱門密碼演進總覽（簡報骨架）
│   ├── papers/               # 單篇論文解析頁
│   ├── concepts/             # 核心概念與指標頁
│   └── comparisons/          # 跨論文對比與爭論頁
└── slides/                   # 最終產出的教學型 HTML 簡報
    └── index.html
```

## 如何在 GitHub 環境中執行

1. **建立 Repository**：將本資料夾上傳至 GitHub（建議設為 Public 以便啟用免費 GitHub Pages）。
2. **先討論、後生成（Ingest 5 篇論文）**：
   - 將找到的 5 篇論文 PDF 或摘要放入 `raw/`。
   - 依循 `AGENTS.md` 規範，逐篇與 LLM 討論重點後寫入 `wiki/`，並同步更新 `index.md` 與 `log.md`。
3. **生成教學 HTML 簡報**：
   - 指示 LLM 讀取 `wiki/` 生成 `slides/index.html`。
4. **啟用 GitHub Pages 展示**：
   - 前往 GitHub Repo 的 **Settings → Pages → Build and deployment**，將 Source 設為 **GitHub Actions**。
   - 推送後，`.github/workflows/deploy-pages.yml` 會自動將 `slides/` 部署為可公開瀏覽的網頁簡報。
