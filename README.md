<h1 align="center">🕸️ AI 風險知識圖譜導航版</h1>
<h3 align="center">AI Risk Navigator</h3>

<p align="center">
  <em>探索式 AI 風險知識圖譜 — 209 個風險情境、4 大應用場景、5 階段資料流、跨框架整合</em>
</p>

<p align="center">
  <a href="https://peterbear8.github.io/Ai-risk-knowledge-graph/">
    <img src="https://img.shields.io/badge/🔗_Live_Demo-Open_Navigator-c24d2c?style=for-the-badge" alt="Live Demo">
  </a>
  <a href="https://www.linkedin.com/in/peterpantw/">
    <img src="https://img.shields.io/badge/LinkedIn-Peter_Pan-0077b5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-3da639?style=for-the-badge" alt="License">
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Risks-209-f85149" alt="Risks">
  <img src="https://img.shields.io/badge/Scenarios-4-ff7b32" alt="Scenarios">
  <img src="https://img.shields.io/badge/Domains-6-d4a72c" alt="Domains">
  <img src="https://img.shields.io/badge/Frameworks-8+-a371f7" alt="Frameworks">
  <img src="https://img.shields.io/badge/Tech-D3.js_v7-39c5bb" alt="D3.js">
  <img src="https://img.shields.io/badge/Theme-Light_/_Dark-58a6ff" alt="Theme">
</p>

<p align="center">
  <strong>Designed by Peter Pan（潘世鳴）</strong> 
</p>

---

## 📖 目錄

- [💡 為什麼要做這個？](#-為什麼要做這個)
- [🔗 線上展示](#-線上展示)
- [📊 圖譜規模](#-圖譜規模)
- [🎯 4 大企業應用場景](#-4-大企業應用場景)
- [🏗️ 分類體系：AIRT-TAXONOMY v7](#️-分類體系airt-taxonomy-v7)
- [🔍 核心互動功能](#-核心互動功能)
- [📐 多維度標註](#-多維度標註)
- [🇹🇼 台灣法規整合](#-台灣法規整合)
- [🛠️ 技術棧](#️-技術棧)
- [📚 參考框架](#-參考框架)
- [🎬 Demo 腳本建議](#-demo-腳本建議)
- [📅 版本演進](#-版本演進)
- [🤝 關於作者](#-關於作者)
- [📄 License](#-license)
- [🙏 致謝](#-致謝)

---

## 💡 為什麼要做這個？

國際 AI 治理框架（ISO 42001、NIST AI RMF、EU AI Act、MITRE ATLAS、OWASP LLM Top 10、CoSAI、台灣 AI 基本法）各自精彩，但對導入 AI 的企業來說：

- 🔍 **看得到框架，看不到風險長相** — 條文太抽象、難以對應到實際場景
- 🔗 **看得到單點風險，看不到鏈路** — 一個風險如何觸發另一個？最終損害是什麼？
- 🎯 **看得到通用論述，看不到場景差異** — RAG 的風險和 Agentic AI 的風險根本不同

風險原本就不是靜態存在Excel或是檢查表內，而應該是動態存在於工作流程中。當Agentic AI 進入企業工作流程(Workflow)後，更加重AI風險識別的困難度。所以我發展互動式 AI 風險知識圖譜(繁體中文)。

> **這個導航版的目標**：以「**企業實際應用場景**」為敘事主軸，把抽象的框架條文落實為**可看、可探、可對話**的風險知識圖譜。

---

## 🔗 線上展示

> 👉 **[點此開啟導航版](https://peterbear8.github.io/Ai-risk-knowledge-graph/)**

---

## 📊 圖譜規模

<table>
  <thead>
    <tr><th>項目</th><th align="right">數量</th></tr>
  </thead>
  <tbody>
    <tr><td>風險情境（合計）</td><td align="right"><b>209</b></td></tr>
    <tr><td>應用場景</td><td align="right"><b>4 大類</b></td></tr>
    <tr><td>資料流階段</td><td align="right"><b>每場景 5 階段</b></td></tr>
    <tr><td>風險領域</td><td align="right"><b>6 大領域（D1-D6）</b></td></tr>
    <tr><td>子領域</td><td align="right"><b>24</b></td></tr>
    <tr><td>整合框架</td><td align="right"><b>8+ 國際標準</b></td></tr>
  </tbody>
</table>

---

## 🎯 4 大企業應用場景

每個場景配有自己的 **5 階段資料流**與獨立的風險鏈路：

<details open>
<summary><b>🟦 通用企業 RAG</b></summary>

| 階段 | 主要風險焦點 |
| :--- | :--- |
| 1️⃣ 資料輸入 → 2️⃣ 向量化儲存 → 3️⃣ 檢索 → 4️⃣ 輸出使用 → 5️⃣ 治理合規 | 知識庫投毒、PII 索引化、提示注入、幻覺、第三方責任邊界 |

</details>

<details>
<summary><b>🤖 Agentic AI 客服</b></summary>

| 階段 | 主要風險焦點 |
| :--- | :--- |
| 1️⃣ 意圖識別 → 2️⃣ 工具選擇 → 3️⃣ 動作執行 → 4️⃣ 結果驗證 → 5️⃣ 回覆生成 | 工具濫用、權限越界、責任歸屬、自主決策邊界 |

</details>

<details>
<summary><b>💻 AI 程式碼審查</b></summary>

| 階段 | 主要風險焦點 |
| :--- | :--- |
| 1️⃣ 程式碼輸入 → 2️⃣ 上下文檢索 → 3️⃣ 模式比對 → 4️⃣ 風險評分 → 5️⃣ 建議生成 | 智財外洩、漏洞模式漏判、授權合規、開發者過度依賴 |

</details>

<details>
<summary><b>💳 AI 詐騙偵測</b></summary>

| 階段 | 主要風險焦點 |
| :--- | :--- |
| 1️⃣ 交易進來 → 2️⃣ 特徵萃取 → 3️⃣ 模型評分 → 4️⃣ 人工複查 → 5️⃣ 警示出件 | 模型偏見、誤報癱瘓、漏報重大損失、可解釋性、監管通報 |

</details>

---

## 🏗️ 分類體系：

| 領域 | 名稱 | 涵蓋範圍 |
| :---: | :--- | :--- |
| **D1** | 資料與隱私風險 | 資料投毒、偏見、隱私洩露、未授權使用 |
| **D2** | 模型安全風險 | 對抗攻擊、提示注入、模型竊取、幻覺 |
| **D3** | 系統與基礎設施風險 | 供應鏈、來源篡改、部署環境、資源濫用 |
| **D4** | 應用與互動風險 | 失控行為、過度依賴、輸出濫用、多智能體 |
| **D5** | 公平與倫理風險 | 演算法歧視、透明度、人類自主性、有害內容 |
| **D6** | 治理與合規風險 | 合規缺口、問責不足、社會衝擊、環境影響 |

---

## 🔍 核心互動功能

### 🗺️ 圖譜瀏覽

- **拖曳與縮放** — D3 力導向圖譜，自由探索結構
- **點擊節點** — 右側面板顯示完整風險詳情（描述、嚴重度、控制建議、框架對應）
- **階段聚焦** — 點按左側階段卡片，圖譜依階段高亮
- **情境切換** — 頂部挑選展示 4 個情境 tab，秒切換至對應風險鏈路

### 🤖 智能分析（NLP 探索）

- **自然語言提問** — 描述你的 AI 應用情境（例：「銀行內部部署 RAG 員工查詢規章」）
- **AI 即時匹配** — 從 209 筆風險中自動找出最相關的 5~6 個風險
- **跨情境跳轉** — 結果中點任一風險，自動切換到對應情境並高亮節點
- **離線示範模式** — 預設離線運作（關鍵字+語意 boost），不需任何 API Key

### 🌓 主題切換

- **亮色 / 深色雙主題** — 點右上角 ☀ / ☾，支援系統偏好自動跟隨
- **localStorage 記憶** — 下次造訪自動套用上次選擇

---
<details>
<summary><b>3 大風險類型</b></summary>

- 技術設計缺陷
- 部署操作與人機互動
- 社會結構與環境衝擊

</details>

## 📚 參考框架

本知識圖譜的風險條目與分類，整合自以下國際與本土框架：

<table>
<tr>
<td>

**🌐 國際標準**
- ISO/IEC 42001 — AI 管理系統
- ISO/IEC 23894 — AI 風險管理
- ISO/IEC 5338 — AI 系統生命週期
- ISO/IEC 22989 — AI 概念與術語

</td>
<td>

**📋 治理框架**
- ISO/IEC 22989 — AI 概念與術語
- ISO/IEC 42001（AI 管理系統）
- ISO/IEC 23894（AI 風險管理）
- ISO/IEC 5338（AI 系統生命週期）
- NIST AI RMF（AI 風險管理框架）
- NIST CSF（網路安全管理框架）
- CoSAI Risk Map（AI 安全風險地圖）
- MITRE ATLAS（AI 對抗威脅）
- AIDEFEND(開源人工智慧防禦框架)
- OWASP LLM Top 10

</td>
</tr>
</table>

## 📅 版本演進

| 版本 | 規模 | 重點 |
| :---: | :--- | :--- |
| **v1.3** | 120 風險 / 1 圖 / 靜態 | 初版分類與框架對應 |
| **v2.0** | 209 風險 / 4 情境 / 互動 | 場景化敘事 + NLP + 主題切換 |

---

## 🤝 關於作者

<table>
<tr>
<td width="200" align="center" valign="middle">
  <br>
  <b>Peter Pan</b><br>
  <em>潘世鳴(Peter Pan)</em><br>
  <br>
  <a href="https://www.linkedin.com/in/peterpantw/">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0077b5?logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <br><br>
</td>
<td valign="middle">

- LinkedIn：[https://www.linkedin.com/in/peterpantw/](https://www.linkedin.com/in/peterpantw/)
> *「我不只告訴你 AI 治理應該怎麼做，我自己用 AI 把工具做出來，並且能教你怎麼做。」*

</td>
</tr>
</table>

---

## 📄 License

[![MIT](https://img.shields.io/badge/License-MIT-3da639?style=for-the-badge)](LICENSE)

MIT License — 歡迎自由使用、修改、分享。引用時請保留作者標示。

---

## 🙏 致謝

> 本知識圖譜的 209 筆風險條目，整合自多個國際開源框架的論述與分類體系。感謝這些社群讓 AI 治理的知識公共化。

---

<p align="center">
  <sub>Made with ☕ and a lot of curiosity by <a href="https://www.linkedin.com/in/peterpantw/">Peter Pan（潘世鳴）</a></sub>
</p>
