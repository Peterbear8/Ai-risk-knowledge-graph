# AI Risk Taxonomy v1 — 分類體系設計文件

**文件編號**: AIRT-TAXONOMY-v1  
**建立日期**: 2026-03-14  
**作者**: Peter（架構決策）+ Claude（設計草案）  
**狀態**: 🔶 待 Peter 審閱  

---

## 1. 設計背景與目標

### 1.1 為什麼需要全新的分類體系？

現有主流 AI 風險分類框架各有侷限：

| 框架 | 優點 | 不足 |
|------|------|------|
| ISO 23894 R1-R8 | 國際標準認可、治理導向 | 粒度太粗，8 類無法區分技術性風險差異 |
| MIT AI Risk Repository（7 領域 / 26 子領域） | 覆蓋全面、學術嚴謹 | 偏社會影響面，對工程團隊不夠 actionable |
| CoSAI Risk Map（4 層） | 技術架構導向、安全實務性強 | 不涵蓋倫理、公平性、隱私等治理議題 |
| MITRE ATLAS | 攻擊手法細緻、威脅情報等級 | 純攻防視角，不涵蓋非惡意風險 |
| OWASP LLM Top 10 | 開發者友善、聚焦 LLM | 範圍限於 LLM，不涵蓋傳統 ML 和 Agent |
| 台灣數發部框架（2026） | 接軌台灣法規、檢核表實用 | 分類粒度粗（僅 3 大類型），尚在草案階段 |

本分類體系的目標是**融合以上框架的優點**，建立一套：
- 依風險本質分類（而非依框架來源）
- 同時覆蓋技術安全與治理合規
- 支援多維度交叉篩選（Actor / Timing / AI System Type / Industry）
- 可對應回各主流框架及台灣法規的映射欄位
- 適合知識圖譜視覺化呈現

### 1.2 專案定位

- **用途**: 個人作品展示，展現跨框架整合能力
- **產品形態**: 靜態互動式知識圖譜網站（Phase A），未來可整合進 Panda / AI-GRC（Phase B）
- **語言**: 中文為主、英文為輔
- **核心查詢場景**: 依 AI 系統架構查詢相關風險（如「RAG 架構有哪些風險」）

---

## 2. 頂層架構：6 大風險領域

```
AI Risk Taxonomy v1
│
├── D1 資料與隱私風險 (Data & Privacy Risks)
├── D2 模型安全風險 (Model Security Risks)
├── D3 系統與基礎設施風險 (System & Infrastructure Risks)
├── D4 應用與互動風險 (Application & Interaction Risks)
├── D5 公平與倫理風險 (Fairness & Ethics Risks)
└── D6 治理與合規風險 (Governance & Compliance Risks)
```

設計邏輯：D1-D4 沿著 AI 系統的技術架構層（資料→模型→基礎設施→應用）展開，對應 CoSAI 的四層結構；D5-D6 覆蓋非技術面的倫理與治理議題，確保分類的完整性。

---

## 3. 完整領域與子領域定義

### D1 資料與隱私風險 (Data & Privacy Risks)

> 涵蓋 AI 系統在資料收集、處理、儲存、使用過程中產生的風險。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D1.1 | 資料投毒 | Data Poisoning | 訓練資料被惡意注入有害樣本，導致模型行為偏離預期。包含標籤翻轉、後門植入、資料集污染等攻擊手法 |
| D1.2 | 訓練資料偏見 | Training Data Bias | 訓練資料中存在的系統性偏差，導致模型對特定群體產生不公平的預測或決策 |
| D1.3 | 隱私洩露與推斷 | Privacy Leakage & Inference | AI 系統記憶並洩露訓練資料中的敏感個人資訊，或透過推斷未經授權地揭露私人屬性 |
| D1.4 | 未授權資料使用 | Unauthorized Data Usage | 未經適當授權或同意即使用受保護資料進行訓練或推論，涉及智慧財產權與資料合規 |

### D2 模型安全風險 (Model Security Risks)

> 涵蓋針對 AI 模型本身的攻擊、模型固有的安全弱點，以及模型輸出的可靠性問題。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D2.1 | 對抗攻擊 | Adversarial Attacks | 透過精心設計的輸入擾動來欺騙模型做出錯誤判斷，包含逃逸攻擊、目標攻擊等 |
| D2.2 | 提示注入 | Prompt Injection | 透過惡意提示操控 LLM 的行為，繞過安全限制或執行未授權的指令。包含直接注入和間接注入 |
| D2.3 | 模型竊取與逆向工程 | Model Extraction & Reverse Engineering | 透過大量查詢或側通道攻擊，複製或還原模型的參數、架構或訓練資料 |
| D2.4 | 模型幻覺與不可靠輸出 | Model Hallucination & Unreliable Output | 模型生成看似合理但實際上錯誤或虛構的內容，包含事實性錯誤、虛假引用、推理鏈斷裂 |

### D3 系統與基礎設施風險 (System & Infrastructure Risks)

> 涵蓋 AI 系統的部署環境、供應鏈、基礎設施層面的安全風險。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D3.1 | 供應鏈攻擊 | Supply Chain Attacks | AI 開發工具鏈、第三方模型、預訓練權重、套件依賴中的惡意程式碼或後門 |
| D3.2 | 模型來源篡改 | Model Source Tampering | 模型權重、程式碼或訓練框架在傳輸或儲存過程中被未授權修改 |
| D3.3 | 部署環境安全 | Deployment Environment Security | 模型服務的容器、API 端點、雲端環境中的傳統資安漏洞，被利用來存取或操控 AI 系統 |
| D3.4 | 資源濫用與拒絕服務 | Resource Abuse & Denial of Service | 透過大量或特製請求耗盡 AI 系統的運算資源，或利用 AI 系統的運算能力進行挖礦等濫用 |

### D4 應用與互動風險 (Application & Interaction Risks)

> 涵蓋 AI 系統在實際應用場景中與使用者互動、執行任務時產生的風險。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D4.1 | 失控行為 | Rogue Actions | AI Agent 或自主系統執行超出預期範圍的行動，包含未授權的工具呼叫、檔案操作、資料外洩 |
| D4.2 | 過度依賴與自動化偏見 | Overreliance & Automation Bias | 使用者過度信任 AI 系統的輸出，放棄獨立判斷，導致錯誤決策未被攔截 |
| D4.3 | 輸出濫用與惡意使用 | Output Misuse & Malicious Use | AI 系統的合法輸出被用於有害目的，如深度偽造、自動化詐欺、大規模虛假資訊生成 |
| D4.4 | 多智能體互動風險 | Multi-Agent Interaction Risks | 多個 AI Agent 之間的協作或競爭產生的非預期行為，包含目標衝突、資訊不對稱、串聯失控 |

### D5 公平與倫理風險 (Fairness & Ethics Risks)

> 涵蓋 AI 系統在公平性、透明度、人類自主性等倫理面向的風險。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D5.1 | 演算法歧視 | Algorithmic Discrimination | AI 系統的決策結果對特定群體（種族、性別、年齡等）產生系統性的不公平對待或不平等表現 |
| D5.2 | 透明度與可解釋性不足 | Lack of Transparency & Explainability | AI 系統的決策過程無法被理解、解釋或審計，使利害關係人無法驗證其合理性 |
| D5.3 | 人類自主性侵蝕 | Erosion of Human Autonomy | AI 系統逐步取代人類在關鍵決策中的角色，削弱個人的自主判斷能力和選擇自由 |
| D5.4 | 有害內容生成 | Toxic Content Generation | AI 系統生成或傳播歧視性、暴力性、仇恨性或其他社會有害的內容 |

### D6 治理與合規風險 (Governance & Compliance Risks)

> 涵蓋 AI 系統在組織治理、法規合規、社會經濟影響層面的風險。

| 編號 | 子領域名稱 | 英文 | 說明 |
|------|----------|------|------|
| D6.1 | 監管合規缺口 | Regulatory Compliance Gaps | AI 系統未能符合適用法規（如 EU AI Act、台灣 AI 基本法、個資法）的要求，面臨處罰或營運中斷 |
| D6.2 | 問責機制不足 | Insufficient Accountability | AI 系統的決策缺乏明確的責任歸屬，發生問題時無法追究責任鏈 |
| D6.3 | 社會經濟衝擊 | Socioeconomic Impact | AI 的廣泛部署導致就業替代、經濟不平等加劇、權力集中等社會層面的負面影響 |
| D6.4 | 環境影響 | Environmental Impact | AI 系統的訓練和運作所消耗的能源與碳排放，對環境造成的負面影響 |

---

## 4. 台灣法規整合：數發部 AI 風險分類框架

### 4.1 背景

2026 年 3 月，台灣數發部依據 AI 基本法訂定 AI 風險分類框架草案（預計 3 月底送行政院審查），定義了 7 大原則與 3 大風險類型，並以「AI 風險管理措施檢核表」作為各部會盤點 AI 應用風險的工具。首波部會包括勞動部、金管會、衛福部及教育部。

本分類體系將數發部框架整合為一個**額外的映射維度**，而非改動 D1-D6 的結構。這讓同一份資料可以在「依風險本質」和「依台灣法規」兩種視角之間切換。

### 4.2 數發部 7 大原則 → 本體系映射

| 數發部原則 | 英文對照 | 對應領域 |
|-----------|---------|---------|
| 隱私保護與資料治理 | Privacy Protection & Data Governance | D1 資料與隱私風險 |
| 資安與安全 | Cybersecurity & Safety | D2 模型安全 + D3 系統與基礎設施 |
| 公平與不歧視 | Fairness & Non-discrimination | D5.1 演算法歧視 |
| 透明與可解釋 | Transparency & Explainability | D5.2 透明度與可解釋性不足 |
| 人類自主 | Human Autonomy | D5.3 人類自主性侵蝕 |
| 問責 | Accountability | D6.2 問責機制不足 |
| 永續發展與福祉 | Sustainable Development & Wellbeing | D6.3 社會經濟衝擊 + D6.4 環境影響 |

### 4.3 數發部 3 大風險類型 → 本體系映射

| 風險類型 | 說明 | 對應領域 |
|---------|------|---------|
| 類型 1：技術設計缺陷 | AI 系統本身的技術設計問題 | D1 + D2 + D3 |
| 類型 2：部署操作與人機互動 | 系統部署、操作及人機互動問題 | D4 應用與互動風險 |
| 類型 3：社會結構與環境衝擊 | 廣泛社會結構與環境衝擊 | D5 + D6 |

### 4.4 在知識圖譜上的呈現

採用「預設隱藏、按需切換」的設計策略：

**預設視角（Default）**：依 D1-D6 風險本質分類著色，展示 Peter 的原創分類體系。這是作品的核心，觀看者第一眼看到的就是這個。

**切換開關（Toggle）**：UI 提供「法規視角」切換功能，啟動後：
- **台灣法規原則視角**：節點依 7 大原則重新著色，用半透明圖層疊加或邊框標記
- **風險類型視角**：節點依 3 大類型分為技術/互動/社會三圈

設計原則：
1. 資料層的 `tw_principle` 和 `tw_risk_type` 欄位始終存在，不因視角切換而改變
2. 切換只改變前端渲染邏輯（節點顏色、圖例、分群），不改變圖譜結構
3. 觀看者可以在「我的分類」和「政府框架」之間即時對照，產生跨框架整合的 aha moment

---

## 5. 風險情境維度屬性

每個具體的風險情境（Risk Scenario）帶有以下維度標籤：

### 5.1 Risk Source（風險來源，原 Actor 維度）

| 值 | 英文 | 說明 |
|----|------|------|
| 人類-內部 | Human-Internal | 組織內部人員的疏忽或惡意行為 |
| 人類-外部 | Human-External | 外部攻擊者、競爭對手、惡意使用者 |
| AI 系統 | AI-System | AI 系統自身的特性或缺陷導致 |
| 系統性 | Systemic | 非單一行為者造成，系統設計或社會結構的產物 |

### 5.1b Responsible AI Actor（責任角色，依 NIST AI RMF）

回答「誰應該負責管理這個風險」，對應 NIST AI RMF Appendix A 的 AI Actor 分類：

| 值 | 英文 | 說明 |
|----|------|------|
| AI 設計者 | AI Design | 負責規劃、設計和資料收集處理，包含資料科學家、領域專家、UX 設計師、治理專家等 |
| AI 開發者 | AI Development | 負責模型建構、選擇、校準、訓練和測試，包含 ML 專家、開發者、第三方實體等 |
| AI 部署者 | AI Deployment | 負責系統整合、合規檢查、上線部署，包含系統整合者、軟體開發者、終端使用者等 |
| AI 運營者 | Operation & Monitoring | 負責系統運行、監控和評估產出，包含系統操作者、稽核人員、合規專家等 |
| TEVV 專家 | TEVV | 貫穿全生命週期的測試、評估、驗證和確效專家 |

### 5.2 Timing（生命週期階段，依 ISO/IEC 5338:2023）

| 值 | 英文 | 說明 |
|----|------|------|
| 啟動 | Inception | 識別需求、目標和可行性 |
| 設計與開發 | Design and Development | 定義系統架構、資料流和訓練模型 |
| 驗證與確效 | Verification and Validation | 測試並確認系統滿足需求且按預期執行 |
| 部署 | Deployment | 將系統發布到其操作環境中 |
| 操作與監督 | Operation and Monitoring | 運行系統、記錄活動並監控性能和結果 |
| 重新評估 | Re-evaluation | 評估系統在變化條件下是否繼續滿足目標 |
| 退役 | Retirement | 停用系統並處理長期資料和存取風險 |

### 5.3 AI System Type（AI 系統架構類型）

| 值 | 英文 | 說明 |
|----|------|------|
| 傳統 ML | Traditional ML | 監督式/非監督式學習、分類、迴歸等 |
| 深度學習 | Deep Learning | CNN、RNN、Transformer 等深度神經網路 |
| LLM 應用 | LLM Application | 基於大型語言模型的應用 |
| RAG 系統 | RAG System | 結合檢索與生成的增強式架構 |
| AI Agent | AI Agent | 具備自主規劃和工具使用能力的智能代理 |
| 多智能體系統 | Multi-Agent System | 多個 AI Agent 協作的系統 |
| 電腦視覺 | Computer Vision | 影像辨識、物件偵測、影像生成等 |
| 推薦系統 | Recommender System | 個人化推薦引擎 |

### 5.4 Industry（行業別）

| 值 | 英文 |
|----|------|
| 通用 | General |
| 金融 | Finance |
| 醫療 | Healthcare |
| 製造 | Manufacturing |
| 教育 | Education |
| 法律 | Legal |
| 公部門 | Government |

### 5.5 Severity（嚴重程度）

| 等級 | 英文 | 分數 |
|------|------|------|
| 極低 | Negligible | 1 |
| 低 | Low | 2 |
| 中 | Medium | 3 |
| 高 | High | 4 |
| 極高 | Critical | 5 |

---

## 6. 跨框架映射欄位

每個風險情境帶有以下映射欄位：

| 欄位 | 說明 | 範例值 |
|------|------|--------|
| risk_source | 風險來源（誰/什麼導致風險） | "Human-External" |
| responsible_actor | 責任角色（依 NIST AI RMF，誰應管理此風險） | ["AI Development", "TEVV"] |
| cosai_ref | CoSAI Risk Map 對應項 | "Data Poisoning" |
| mitre_atlas_ref | MITRE ATLAS Technique ID | "AML.T0020" |
| owasp_llm_ref | OWASP LLM Top 10 項目 | "LLM03" |
| iso_23894_ref | ISO 23894 風險類別 | "R1", "R2" |
| nist_rmf_ref | NIST AI RMF 維度 | "GOVERN-1.1" |
| mit_repo_ref | MIT AI Risk Repository 子領域 | "2.1" |
| **tw_principle** | **數發部 7 大原則** | **"隱私保護與資料治理"** |
| **tw_risk_type** | **數發部 3 大風險類型** | **1 / 2 / 3** |

---

## 7. 資料庫 Schema 設計（JSON 格式）

```json
{
  "taxonomy_version": "1.0",
  "language": "zh-TW",
  "domains": [
    {
      "id": "D1",
      "name_zh": "資料與隱私風險",
      "name_en": "Data & Privacy Risks",
      "color": "#4A90D9",
      "tw_risk_type": 1,
      "subdomains": [
        {
          "id": "D1.1",
          "name_zh": "資料投毒",
          "name_en": "Data Poisoning",
          "description_zh": "訓練資料被惡意注入有害樣本...",
          "description_en": "Malicious injection of harmful samples..."
        }
      ]
    }
  ],
  "scenarios": [
    {
      "id": "RS-D1.1-001",
      "subdomain": "D1.1",
      "title_zh": "標籤翻轉攻擊導致分類模型誤判",
      "title_en": "Label flipping attack causes misclassification",
      "description_zh": "攻擊者透過修改訓練資料中的標籤...",
      "risk_source": "Human-External",
      "responsible_actor": ["AI Development", "TEVV"],
      "timing": ["Design and Development"],
      "ai_system_type": ["Traditional ML", "Deep Learning"],
      "industry": ["General"],
      "severity": 4,
      "controls": ["C-D1.1-001", "C-D1.1-002"],
      "framework_mapping": {
        "cosai_ref": "Data Poisoning",
        "mitre_atlas_ref": "AML.T0020",
        "owasp_llm_ref": null,
        "iso_23894_ref": "R2",
        "nist_rmf_ref": "MAP-2.3",
        "mit_repo_ref": "2.2",
        "tw_principle": ["資安與安全"],
        "tw_risk_type": 1
      }
    }
  ],
  "controls": [
    {
      "id": "C-D1.1-001",
      "name_zh": "訓練資料完整性驗證",
      "name_en": "Training Data Integrity Verification",
      "type": "Preventive",
      "description_zh": "在模型訓練前驗證資料來源的可信度...",
      "framework_ref": ["ISO 42001 A.7.3", "NIST MAP-2.3"]
    }
  ]
}
```

### 7.1 編號規則

- 風險情境: `RS-{領域}.{子領域}-{三位數序號}`（如 `RS-D2.2-003`）
- 控制措施: `C-{領域}.{子領域}-{三位數序號}`（如 `C-D2.2-002`）

---

## 8. 知識圖譜節點與邊定義

### 8.1 節點類型 (Node Types)

| 節點類型 | 說明 | 視覺化 |
|---------|------|--------|
| Domain | 頂層風險領域 | 大節點，領域專屬顏色 |
| Subdomain | 子領域 | 中節點，繼承領域顏色（淺色） |
| Scenario | 風險情境 | 小節點，大小依 severity |
| Control | 控制措施 | 菱形節點，綠色系 |
| AISystemType | AI 系統架構類型 | 六角形節點，紫色系 |
| Framework | 外部框架參考 | 方形節點，灰色系 |
| TW_Principle | 數發部 7 大原則 | 圓角方形節點，橘色系 |

### 8.2 邊類型 (Edge Types)

| 邊類型 | 方向 | 說明 | 視覺化 |
|--------|------|------|--------|
| belongs_to | Scenario → Subdomain | 風險情境歸屬於子領域 | 實線 |
| part_of | Subdomain → Domain | 子領域歸屬於領域 | 實線（粗） |
| mitigated_by | Scenario → Control | 可被控制措施緩解 | 綠色虛線 |
| affects | Scenario → AISystemType | 影響的系統架構類型 | 紫色實線 |
| maps_to | Scenario → Framework | 對應到外部框架 | 灰色虛線 |
| governed_by | Scenario → TW_Principle | 受數發部原則規範 | 橘色虛線 |
| related_to | Scenario → Scenario | 風險情境間的關聯 | 橘色虛線 |

---

## 9. 風險情境數量估算

| 領域 | 子領域數 | 預估情境數 | 說明 |
|------|---------|----------|------|
| D1 資料與隱私 | 4 | 20-30 | 資料面風險相對集中 |
| D2 模型安全 | 4 | 30-40 | 技術攻擊手法多樣 |
| D3 系統與基礎設施 | 4 | 15-25 | 偏傳統資安延伸 |
| D4 應用與互動 | 4 | 25-35 | Agent / 多智能體是新興熱區 |
| D5 公平與倫理 | 4 | 20-25 | 偏質性描述 |
| D6 治理與合規 | 4 | 15-20 | 偏制度層面 |
| **合計** | **24** | **125-175** | MVP 目標：每子領域 5-7 個情境 |

---

## 10. 與現有專案的關係

### 10.1 與 Panda 的關係

| 本體系 | ISO 23894 映射 |
|--------|---------------|
| D1 資料與隱私 | R1（隱私保護與資料治理） |
| D2 模型安全 | R2（網路安全與安全性） |
| D3 系統與基礎設施 | R2（網路安全與安全性） |
| D4 應用與互動 | R5（技術穩健性）、R7（人類監督） |
| D5 公平與倫理 | R3（公平性）、R4（透明度） |
| D6 治理與合規 | R6（問責性）、R8（永續發展） |

### 10.2 與 AI-GRC 的關係

可透過 `nist_rmf_ref` 映射到 AI-GRC 的 NIST 九維度。未來 Phase B 整合時，知識圖譜可作為 MCP Resource 供 AI-GRC 查詢。

---

## 11. 待 Peter 確認事項

請逐項確認或標註修改意見：

- [x] **6 個頂層領域**的劃分 — 已確認
- [x] **24 個子領域**覆蓋完整性 — 已確認
- [x] **Actor 維度**：已拆分為雙維度 — Risk Source（4 值，風險來源）+ Responsible AI Actor（5 值，依 NIST AI RMF）
- [x] **Timing 維度**：已採用 ISO 5338 七階段（Inception → Design & Development → V&V → Deployment → Operation & Monitoring → Re-evaluation → Retirement）
- [x] **AI System Type 維度**的 8 個值 — 已確認
- [x] **Industry 維度**的 7 個行業 — 已確認
- [x] **數發部 7 大原則映射** — 已確認映射正確，資料層保留 `tw_principle` 欄位，UI 預設隱藏，透過「法規視角」切換開關按需呈現
- [x] **數發部 3 大風險類型映射** — 已確認映射合理，資料層保留 `tw_risk_type` 欄位，同上以切換方式呈現
- [x] **JSON schema 設計** — 已確認
- [x] **知識圖譜節點/邊定義** — 已確認
- [x] **風險情境數量**（125-175 個）MVP 規模 — 已確認

---

**審閱完成後 → Claude 開始 Phase 2（本體設計細化）→ Phase 3（資料填充）**
