# K-Pop 熱門密碼與歌曲結構演進總覽

> **狀態**：骨架已建立，待 Ingest 5 篇論文後逐步充實數據與實證結論。
> **教學定位**：本頁將作為最終教學型 HTML 簡報（`slides/index.html`）的核心敘事腳本，協助零基礎讀者理解「資料科學家如何用數據拆解 K-Pop 熱門歌曲」。

## 1. 什麼是熱門歌曲科學 (Hit Song Science, HSS)？
- 利用音樂資訊檢索（MIR）技術，將旋律、節奏、音色轉化為量化特徵（如 [Audio Features](concepts/audio-features.md)），並透過機器學習預測歌曲登上排行榜的機率。

## 2. K-Pop 音樂結構的三階段演進（待論文數據填入）
1. **經典洗腦時期（二代～三代團）**：重複性 Hook 與強烈節奏設計（見 [Hook Theory](concepts/hook-theory.md)）。
2. **全球化擴張時期（三代末～四代團）**：英文比例上升與跨文化曲風融合，本土與海外榜單偏好出現分化（見 [Melon vs. Spotify](comparisons/melon-vs-spotify.md)）。
3. **短影音演算法時期（四代末～五代團）**：受 Reels / Shorts / TikTok 驅動，前奏縮短、副歌前置、總曲長壓縮至 2 分 30 秒內（見 [The TikTok Effect](concepts/tiktok-effect.md)）。

## 3. 預測模型的演進：從單一音訊到多模態
- 早期模型僅依賴音訊特徵；最新研究則結合歌詞語意與視覺編舞記憶點（見 [Audio vs. Multimodal](comparisons/audio-vs-multimodal.md)）。
