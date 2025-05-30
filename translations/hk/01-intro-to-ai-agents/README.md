<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "d84943abc8f001ad4670418d32c2d899",
  "translation_date": "2025-05-20T07:34:26+00:00",
  "source_file": "01-intro-to-ai-agents/README.md",
  "language_code": "hk"
}
-->
與其他學習者及 AI Agent 建造者交流，並隨時提出你對本課程的任何疑問。

開始本課程前，我們先深入了解什麼是 AI Agents，以及如何將它們應用於我們所建構的應用程式和工作流程中。

## 介紹

本課涵蓋：

- 什麼是 AI Agents，以及不同類型的 Agents？
- AI Agents 最適合用於哪些案例，它們如何幫助我們？
- 設計 Agentic 解決方案時的一些基本組件是什麼？

## 學習目標
完成本課後，你應該能夠：

- 理解 AI Agent 的概念，以及它們與其他 AI 解決方案的不同之處。
- 更有效地應用 AI Agents。
- 為用戶和客戶設計出具生產力的 Agentic 解決方案。

## 定義 AI Agents 及 AI Agents 的類型

### 什麼是 AI Agents？

AI Agents 是一套 **系統**，讓 **大型語言模型（LLMs）** 能夠透過擴充其功能，並賦予 LLMs **使用工具** 和 **知識** 的能力，從而 **執行動作**。

我們來拆解這個定義：

- **系統** — 重要的是要把 Agents 視為由多個組件組成的系統，而不只是單一組件。AI Agent 的基本組件包括：
  - **環境** — AI Agent 運作的特定空間。例如，假設我們有一個旅遊訂票 AI Agent，環境可能就是 AI Agent 用來完成任務的旅遊訂票系統。
  - **感測器** — 環境中有資訊並會提供回饋。AI Agents 利用感測器來收集並解讀環境當前狀態的資訊。在旅遊訂票 Agent 的例子中，訂票系統可提供酒店房態或航班價格等資訊。
  - **執行器** — 當 AI Agent 獲得環境的當前狀態後，針對當前任務決定執行什麼動作來改變環境。對旅遊訂票 Agent 來說，可能是為用戶預訂一間可用的房間。

![What Are AI Agents?](../../../translated_images/what-are-ai-agents.125520f55950b252a429b04a9f41e0152d4dafa1f1bd9081f4f574631acb759e.hk.png)

**大型語言模型** — Agent 的概念在 LLMs 出現前就存在。使用 LLMs 建造 AI Agents 的優勢在於它們能理解人類語言及資料，這使 LLMs 能解讀環境資訊並制定改變環境的計劃。

**執行動作** — 在 AI Agent 系統外，LLMs 的動作通常限於根據用戶提示產生內容或資訊；在 AI Agent 系統內，LLMs 能透過解讀用戶請求，並使用環境中可用的工具來完成任務。

**使用工具** — LLM 可使用的工具由 1) 它運作的環境，及 2) AI Agent 的開發者所定義。以旅遊 Agent 為例，Agent 可用的工具受限於訂票系統的操作，或開發者可限制 Agent 只能使用訂航班的工具。

**記憶與知識** — 記憶可指對話中用戶與 Agent 間的短期記憶；長期來說，除了環境提供的資訊外，AI Agents 亦可從其他系統、服務、工具甚至其他 Agents 中擷取知識。旅遊 Agent 的例子中，這些知識可能是存放於客戶資料庫中用戶的旅遊偏好資訊。

### 不同類型的 Agents

既然我們已經有 AI Agents 的一般定義，現在來看看一些特定的 Agent 類型，以及它們如何應用於旅遊訂票 AI Agent。

| **Agent 類型**                | **描述**                                                                                                                       | **範例**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **簡單反射型 Agents**      | 根據預設規則立即執行動作。                                                                                  | 旅遊 Agent 解讀電郵內容，並將旅遊投訴轉交客戶服務部。                                                                                                                          |
| **基於模型的反射型 Agents** | 根據對世界的模型及模型變化執行動作。                                                              | 旅遊 Agent 根據歷史價格資料，優先處理價格有重大變動的路線。                                                                                                             |
| **目標導向 Agents**         | 透過解讀目標並制定達成目標的行動計劃來執行任務。                                  | 旅遊 Agent 透過決定從當前地點到目的地所需的交通安排（汽車、大眾運輸、航班）來預訂行程。                                                                                |
| **效用導向 Agents**      | 考慮偏好並以數值權衡取捨，決定如何達成目標。                                               | 旅遊 Agent 在預訂旅程時權衡便利性與成本，以最大化效用。                                                                                                                                          |
| **學習型 Agents**           | 透過回饋不斷改進並調整行動。                                                        | 旅遊 Agent 根據旅程後的顧客調查回饋，優化未來的訂票安排。                                                                                                               |
| **階層型 Agents**       | 由多個 Agents 組成分層系統，高階 Agent 將任務拆分為子任務，交由低階 Agent 完成。 | 旅遊 Agent 將取消行程任務拆分為多個子任務（如取消特定訂位），由低階 Agents 完成，並回報給高階 Agent。                                     |
| **多 Agent 系統 (MAS)** | Agents 獨立完成任務，可能合作或競爭。                                                           | 合作：多個 Agents 分別負責預訂酒店、航班和娛樂服務。競爭：多個 Agents 競爭管理同一酒店的訂房日曆，爭取為顧客訂房。 |

## 何時使用 AI Agents

在前面部分，我們以旅遊 Agent 案例說明不同 Agent 類型如何用於旅遊訂票的不同情境。整個課程中，我們將持續使用這個應用場景。

來看看 AI Agents 最適合用於哪些案例：

![When to use AI Agents?](../../../translated_images/when-to-use-ai-agents.912b9a02e9e0e2af45a3e24faa4e912e334ec23f21f0cf5cb040b7e899b09cd0.hk.png)

- **開放式問題** — 讓 LLM 判斷完成任務所需步驟，因為這些步驟不一定能硬編碼於工作流程中。
- **多步驟流程** — 需要一定複雜度的任務，AI Agent 需在多個回合中使用工具或資訊，而非一次性檢索。
- **隨時間改善** — Agent 能透過環境或用戶回饋持續優化表現，以提供更佳效用。

我們會在「建立可信賴 AI Agents」課程中探討更多使用 AI Agents 的考量。

## Agentic 解決方案基礎

### Agent 開發

設計 AI Agent 系統的第一步是定義工具、動作與行為。本課程重點使用 **Azure AI Agent 服務** 來定義我們的 Agents。此服務提供功能包括：

- 選用 OpenAI、Mistral、Llama 等開放模型
- 透過 Tripadvisor 等供應商使用授權資料
- 使用標準化 OpenAPI 3.0 工具

### Agentic 模式

與 LLM 互動是透過提示（prompts）完成。由於 AI Agents 具半自主性，環境變化後不一定能或需要手動再次提示 LLM。我們使用 **Agentic 模式**，讓 LLM 能以更具擴展性的方式，分多步驟接收提示。

本課程涵蓋目前較受歡迎的幾種 Agentic 模式。

### Agentic 框架

Agentic 框架讓開發者能透過程式碼實現 agentic 模式，提供範本、插件和工具，促進 AI Agents 間更好的協作。這些優勢提升了 AI Agent 系統的可觀察性與除錯能力。

本課程將探索以研究為導向的 AutoGen 框架，以及適合生產環境的 Semantic Kernel Agent 框架。

## 上一課

[Course Setup](../00-course-setup/README.md)

## 下一課

[Exploring Agentic Frameworks](../02-explore-agentic-frameworks/README.md)

**免責聲明**：  
本文件使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們致力於確保準確性，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而引起的任何誤解或誤釋承擔責任。