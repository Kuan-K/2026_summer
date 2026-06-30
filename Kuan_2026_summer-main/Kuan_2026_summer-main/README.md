# Schedule-and-Goal-Planning
Schedule and Goal Planning

```text
oai-aerial-metanoia-internship/
├── README.md
│
├── lab-handover/
│   └── ming-handover-notes.md
│
├── internship-notes/
│   ├── background/
│   │   ├── 5g-ran-basic-map.md
│   │   ├── oai-l2-basic-role.md
│   │   ├── aerial-cuphy-basic-role.md
│   │   ├── oran-fronthaul-basic.md
│   │   └── glossary.md
│   │
│   ├── reproduce/
│   │   ├── official-manual-annotated.md
│   │   ├── config-file-index.md
│   │   ├── log-file-index.md
│   │   ├── baseline-success-log-summary.md
│   │   └── reproduction-report-for-company.md
│   │
│   ├── e2e-architecture/
│   │   ├── e2e-system-architecture.md
│   │   ├── component-role-table.md
│   │   ├── data-flow-ue-to-cn.md
│   │   ├── control-plane-flow.md
│   │   ├── user-plane-flow.md
│   │   └── layer-by-layer-debug-map.md
│   │
│   ├── oai-l2-cuphy/
│   │   ├── oai-l2-plus-role.md
│   │   ├── fapi-overview.md
│   │   ├── nvipc-overview.md
│   │   ├── oai-to-cuphy-message-flow.md
│   │   ├── slot-timing-notes.md
│   │   ├── oai-config-map.md
│   │   ├── cuphycontroller-yaml-map.md
│   │   └── l2-l1-debug-checklist.md
│   │
│   ├── metanoia-oru-prep/
│   │   ├── metanoia-hardware-profile.md
│   │   ├── metanoia-access-method.md
│   │   ├── metanoia-network-config.md
│   │   ├── metanoia-ptp-config.md
│   │   ├── metanoia-rf-config.md
│   │   ├── metanoia-ecpri-config.md
│   │   ├── metanoia-eaxc-mapping.md
│   │   ├── metanoia-compression-setting.md
│   │   └── metanoia-oru-readiness-checklist.md
│   │
│   ├── metanoia-integration/
│   │   ├── bringup-plan.md
│   │   ├── bringup-daily-log.md
│   │   ├── cuphycontroller-metanoia-yaml-notes.md
│   │   ├── oai-gnb-metanoia-config-notes.md
│   │   ├── ptp-lock-test-result.md
│   │   ├── ecpri-connectivity-test.md
│   │   ├── oru-onair-check.md
│   │   ├── ue-attach-test-result.md
│   │   ├── ping-test-result.md
│   │   ├── iperf-test-result.md
│   │   └── integration-issue-list.md
│   │
│   └── final-report/
│       ├── internship-final-summary.md
│       ├── e2e-architecture-summary.md
│       ├── reproduction-summary.md
│       ├── metanoia-oru-integration-summary.md
│       ├── config-mapping-summary.md
│       ├── test-result-summary.md
│       ├── unresolved-issues.md
│       ├── debug-guide.md
│       └── next-step-recommendation.md
│
├── logs/
│   ├── 2026-06.md
│   ├── 2026-07.md
│   └── 2026-08.md
│
└── issues/
    ├── open-questions.md
    ├── technical-blockers.md
    └── questions-for-company.md
```



| 時間          | 主題                         | 重點                                                                    | 主要產出                                                                                                                                                     |
| ----------- | -------------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 06/26～07/03 | Ming 交接 + E2E 架構第一版        | 完成交接；先完整理解 UE、O-RU、fronthaul、cuPHY、OAI L2+、5GC 的位置                    | `ming-handover-notes.md`, `e2e-system-architecture.md`, `component-role-table.md`, `glossary.md`                                                         |
| 07/04～07/10 | 帶著 E2E 架構重現學長實驗            | 每個 command 都對應到 E2E component；建立 config / log 索引與 baseline            | `senior-experiment-reproduction.md`, `config-file-index.md`, `log-file-index.md`, `baseline-success-log-summary.md`       |
| 07/11～07/17 | 用重現結果修正 E2E 架構             | 把實際 container、config、log 放回 E2E；整理 control plane、user plane、debug map | `control-plane-flow.md`, `user-plane-flow.md`, `layer-by-layer-debug-map.md`, `e2e-architecture.drawio`                                                  |
| 07/18～07/25 | 重現成果收斂                | 完成官方 manual 註解版、重現報告、baseline log summary、問題清單                        | `official-manual-annotated.md`, `reproduction-report-for-company.md`, `questions-for-company.md`, `technical-blockers.md`                                |
| 07/26～08/02 | OAI L2+ ↔ Aerial cuPHY 深入  | 深入 FAPI、NVIPC、cuPHYController、slot timing、config map                  | `fapi-overview.md`, `nvipc-overview.md`, `oai-to-cuphy-message-flow.md`, `slot-timing-notes.md`, `l2-l1-debug-checklist.md`                              |
| 08/03～08/09 | Metanoia O-RU 接入前準備        | 蒐集 Metanoia hardware、network、PTP、RF、eCPRI、eAxC、compression 資訊         | `metanoia-hardware-profile.md`, `metanoia-network-config.md`, `metanoia-ptp-config.md`, `metanoia-oru-readiness-checklist.md`                            |
| 08/10～08/16 | Metanoia O-RU bring-up     | 修改 cuPHYController YAML 與 OAI config；確認 PTP、VLAN、eCPRI、fronthaul      | `bringup-plan.md`, `cuphycontroller-metanoia-yaml-notes.md`, `oai-gnb-metanoia-config-notes.md`, `ptp-lock-test-result.md`, `ecpri-connectivity-test.md` |
| 08/17～08/23 | OTA 驗證與 UE attach          | 確認 O-RU on-air、UE detect cell、RACH、RRC/NAS、PDU session                | `ue-attach-test-result.md`                                                                            |
| 08/24～08/31 | E2E traffic + final report | ping / iperf / debug；整理 final summary、unresolved issues、next step     | `ping-test-result.md`, `iperf-test-result.md`, `internship-final-summary.md`, `debug-guide.md`, `next-step-recommendation.md`                            |




# Repository File Guide
# 1. `lab-handover/`

## `ming-handover-notes.md`

### 目的

記錄 Ming 學長交接的實驗室工作內容。這部分與實習主線分開，只作為實驗室任務交接紀錄。

### 應該包含

* Ming 學長交接的工作內容
* 需要接手的事項
* 相關 server、repo、資料夾、帳號、設備
* 目前狀態
* 後續需要做的事
* 尚未確認的問題

### 完成標準

之後回頭看這份文件，可以知道 Ming 學長交接了什麼、你需要負責什麼、卡住時要問誰。

---

# 2. `internship-notes/background/`

## `5g-ran-basic-map.md`

### 目的

建立 5G RAN 的基本架構地圖，作為理解 OAI L2+、Aerial cuPHY、O-RU 的基礎。

### 應該包含

* UE、gNB、CU、DU、RU、5GC 的關係
* L1、L2、L3 的基本分工
* control plane 與 user plane 的基本概念
* UE attach 的大致流程
* ping / iperf 在 E2E 中代表什麼

### 完成標準

能用一張圖和一段文字說明 UE 到 Core Network 的基本路徑。

---

## `oai-l2-basic-role.md`

### 目的

整理 OAI L2+ 在整個系統中的角色。

### 應該包含

* OAI L2+ 在 E2E 架構中的位置
* OAI L2+ 和 5GC 的關係
* OAI L2+ 和 Aerial cuPHY 的關係
* OAI L2+ 可能負責的功能，例如 MAC、RLC、PDCP、RRC
* OAI L2+ 相關 log 和 config 的位置

### 完成標準

能說明 OAI L2+ 不是 RF，也不是 O-RU，而是 gNB 高層，負責和 Core Network 以及 cuPHY 溝通。

---

## `aerial-cuphy-basic-role.md`

### 目的

整理 Aerial cuPHY / cuBB 在系統中的角色。

### 應該包含

* Aerial cuPHY 在 E2E 架構中的位置
* cuPHY 和 L1 / PHY 的關係
* cuPHYController 的基本角色
* cuPHY 和 OAI L2+ 的關係
* cuPHY 和 fronthaul / O-RU 的關係
* 重要 log 與設定檔

### 完成標準

能說明 Aerial cuPHY 是 GPU 加速的 L1 / PHY，並且透過 cuPHYController 與 OAI L2+、fronthaul、O-RU 連接。

---

## `oran-fronthaul-basic.md`

### 目的

整理 O-RAN fronthaul 的基本概念，為後面 Metanoia O-RU 整合做準備。

### 應該包含

* O-RAN fronthaul 在 E2E 架構中的位置
* eCPRI 是什麼
* C-plane、U-plane、S-plane、M-plane 的基本概念
* VLAN、MAC、PTP 為什麼重要
* O-RU 與 cuPHY 之間需要對齊哪些設定

### 完成標準

能說明 cuPHY 到 O-RU 之間不是一般網路連線，而是需要 eCPRI、VLAN、PTP、MAC、RF 參數等設定對齊。

---

## `glossary.md`

### 目的

建立整個實習期間會遇到的名詞表。

### 應該包含

* 名詞
* 中文解釋
* 英文全名
* 在 E2E 架構中的位置
* 和本實習的關係

### 建議格式

| Term  | Full Name        | 中文說明              | 在架構中的位置       | 備註 |
| ----- | ---------------- | ----------------- | ------------- | -- |
| OAI   | OpenAirInterface | 開源 5G RAN / CN 軟體 | OAI L2+ / 5GC |    |
| cuPHY | CUDA PHY         | NVIDIA GPU 加速 PHY | L1            |    |
| O-RU  | O-RAN Radio Unit | 無線射頻單元            | RU / RF       |    |

### 完成標準

遇到不熟的名詞時，可以回到這份文件快速查到基本意思和它在系統中的位置。

---

# 3. `internship-notes/reproduce/`

## `official-manual-annotated.md`

### 目的

把官方安裝手冊改寫成自己的註解版，不只是複製指令，而是說明每一步在 E2E 架構中的意義。

### 應該包含

* 官方手冊步驟
* 實際執行指令
* 對應的 E2E component
* 這一步的目的
* 使用到的設定檔
* 產生的 log
* 成功時應看到什麼
* 遇到的問題與解法

### 完成標準

別人照這份文件不只知道怎麼跑，也能知道每個步驟在整個系統中代表什麼。

---


## `config-file-index.md`

### 目的

整理所有重要設定檔的位置、用途與關鍵參數。

### 應該包含

* 設定檔路徑
* 所屬元件
* 主要用途
* 重要參數
* 修改紀錄
* 是否會影響 Metanoia O-RU 整合

### 建議格式

| Config File          | Component    | Purpose               | Important Parameters    | Notes |
| -------------------- | ------------ | --------------------- | ----------------------- | ----- |
| OAI gNB config       | OAI L2+      | cell / PLMN / band 設定 | MCC, MNC, band, SCS     |       |
| cuphycontroller YAML | Aerial cuPHY | fronthaul / O-RU 設定   | NIC, VLAN, dst_mac_addr |       |

### 完成標準

後續要改設定時，可以快速知道要改哪個檔案、哪個參數、會影響哪一層。

---

## `log-file-index.md`

### 目的

整理所有重要 log 的來源與用途。

### 應該包含

* log 來源
* log 路徑
* 對應元件
* 可以用來判斷什麼問題
* 成功時常見 log
* 失敗時常見 log

### 建議格式

| Log Source  | Path / Command | Component    | 用途                           |
| ----------- | -------------- | ------------ | ---------------------------- |
| OAI gNB log |                | OAI L2+      | 看 RRC、MAC、FAPI、UE attach     |
| cuPHY log   |                | Aerial cuPHY | 看 L1、slot、fronthaul、preamble |
| CN log      |                | 5GC          | 看 registration、PDU session   |

### 完成標準

debug 時能快速知道要看哪個 log，而不是每次重新找。

---

## `baseline-success-log-summary.md`

### 目的

整理重現學長實驗時的 baseline 成功證據。

### 應該包含

* 成功跑到哪一步
* 每個 component 的成功指標
* 對應 log 片段
* 對應截圖或輸出
* 尚未成功的部分
* 後續需要確認的問題

### 建議格式

| Component       | Success Indicator       | Evidence              | Status |
| --------------- | ----------------------- | --------------------- | ------ |
| OAI L2+         | gNB process started     | log line / screenshot | Pass   |
| cuPHYController | no fatal error          | log line              | Pass   |
| 5GC             | AMF / SMF / UPF running | docker ps             | Pass   |

### 完成標準

公司或學長問「目前重現結果如何」時，可以直接用這份文件回答。

---

## `reproduction-report-for-company.md`

### 目的

整理給公司看的重現報告。

### 應該包含

* 本次重現目的
* 使用環境
* 重現步驟摘要
* 成功結果
* 失敗或卡住的地方
* log / screenshot 證據
* 學到的 E2E 架構重點
* 後續要做什麼

### 完成標準

這份文件應該可以直接作為週報或階段回報的基礎。

---

# 4. `internship-notes/e2e-architecture/`

## `e2e-system-architecture.md`

### 目的

整理整個 OAI L2+、Aerial cuPHY、Metanoia O-RU、5GC、UE 的端到端架構。

### 應該包含

* E2E 架構圖
* 每個 component 的位置
* control plane / user plane 的大致路徑
* 軟體、硬體、網路之間的關係
* 實際環境中的 container、server、interface、config 對應

### 完成標準

能用這份文件向公司說明整個系統怎麼從 UE 連到 Core Network。

---

## `component-role-table.md`

### 目的

整理每個元件的角色、輸入、輸出與相關文件。

### 應該包含

* component 名稱
* role
* input
* output
* related config
* related log

### 建議格式

| Component | Role      | Input                          | Output             | Related Config | Related Log |
| --------- | --------- | ------------------------------ | ------------------ | -------------- | ----------- |
| UE        | 發起連線與資料傳輸 | RF signal                      | NAS / user data    | SIM profile    | UE log      |
| OAI L2+   | gNB 高層    | FAPI indication / CN signaling | FAPI request / RRC | OAI config     | OAI log     |

### 完成標準

任何一個 component 都能用一行解釋清楚它的用途。

---

## `data-flow-ue-to-cn.md`

### 目的

整理 UE 到 Core Network / Data Network 的整體資料流。

### 應該包含

* UE 到 O-RU
* O-RU 到 cuPHY
* cuPHY 到 OAI L2+
* OAI L2+ 到 5GC
* 5GC 到 Data Network
* ping / iperf 的資料流

### 完成標準

能說明 UE 發出的資料最後如何經過 RAN 和 Core 到達外部網路。

---

## `control-plane-flow.md`

### 目的

整理 control plane 的流程，例如 cell search、RACH、RRC、NAS、registration。

### 應該包含

* UE detect cell
* RACH
* RRC connection
* NAS authentication
* registration
* PDU session establishment
* 對應 log

### 完成標準

UE attach 失敗時，可以用這份文件判斷大概卡在哪一段。

---

## `user-plane-flow.md`

### 目的

整理 user plane 的流程，例如 UE 拿到 IP 後 ping / iperf 的資料路徑。

### 應該包含

* UE user data
* O-RU / cuPHY / OAI L2+
* UPF
* Data Network
* ping / iperf 測試方式
* 可能失敗原因

### 完成標準

ping 或 iperf 不通時，可以用這份文件判斷是 RAN、UPF、routing 還是其他問題。

---

## `layer-by-layer-debug-map.md`

### 目的

建立分層 debug 地圖。

### 應該包含

* 常見現象
* 優先懷疑層級
* 要看哪些 log
* 要查哪些 config
* 下一步 action

### 建議格式

| Symptom           | Possible Layer  | Check Item            | Related Log / Config | Next Action        |
| ----------------- | --------------- | --------------------- | -------------------- | ------------------ |
| UE 看不到 cell       | RF / O-RU / PTP | O-RU on-air, PTP lock | O-RU log             | Check RF config    |
| OAI 起來但 cuPHY 沒反應 | FAPI / NVIPC    | IPC status            | OAI log, cuPHY log   | Check NVIPC config |

### 完成標準

遇到問題時可以照這份文件一步一步定位，而不是憑感覺亂查。

---

# 5. `internship-notes/oai-l2-cuphy/`

## `oai-l2-plus-role.md`

### 目的

深入整理 OAI L2+ 在 OAI + Aerial 架構中的角色。

### 應該包含

* OAI L2+ 的功能
* 和 5GC 的關係
* 和 cuPHY 的關係
* 和 FAPI / NVIPC 的關係
* 重要設定與 log

### 完成標準

能說明 OAI L2+ 在整個 gNB 中負責什麼，以及它如何和 cuPHY 溝通。

---

## `fapi-overview.md`

### 目的

整理 FAPI 的基本概念與常見訊息。

### 應該包含

* FAPI 是什麼
* 為什麼 L2/L1 需要 FAPI
* 常見 FAPI message
* DL_TTI、UL_TTI、TX_DATA、RX_DATA、CRC、UCI、RACH 的概念
* FAPI 和 OAI / cuPHY 的關係

### 完成標準

能用自己的話說明 OAI L2+ 如何透過 FAPI 把排程與資料交給 cuPHY。

---

## `nvipc-overview.md`

### 目的

整理 NVIPC 在 OAI + Aerial 整合中的角色。

### 應該包含

* NVIPC 是什麼
* 它連接哪兩個 process / container
* 傳遞哪些資料
* 和 FAPI 的關係
* build 或 runtime 中和 NVIPC 有關的指令與 log

### 完成標準

能說明 NVIPC 是 OAI L2+ 和 Aerial cuPHY 之間的重要 IPC 橋接。

---

## `oai-to-cuphy-message-flow.md`

### 目的

整理 OAI L2+ 到 cuPHY 的訊息流程。

### 應該包含

* OAI L2+ 發出的訊息
* FAPI message 流向
* NVIPC 傳輸方式
* cuPHYController 接收後做什麼
* cuPHY 如何回 indication
* 對應 log

### 完成標準

能畫出 OAI L2+ → FAPI/NVIPC → cuPHYController → cuPHY 的基本流程。

---

## `slot-timing-notes.md`

### 目的

整理 5G slot timing 對 OAI L2+ 與 cuPHY 整合的影響。

### 應該包含

* frame / subframe / slot 基本概念
* numerology / SCS 對 slot duration 的影響
* DL / UL slot timing
* timing mismatch 可能造成的問題
* 相關 log 或錯誤現象

### 完成標準

能說明為什麼 L2、L1、O-RU 必須在時間上對齊。

---

## `oai-config-map.md`

### 目的

整理 OAI gNB config 中重要參數。

### 應該包含

* PLMN
* TAC
* band
* ARFCN / frequency
* bandwidth
* SCS
* TDD pattern
* 5GC IP / AMF connection
* 和 Metanoia O-RU 需要對齊的項目

### 完成標準

接 Metanoia O-RU 前，可以知道 OAI config 裡哪些欄位會影響 RF、cell、Core connection。

---

## `cuphycontroller-yaml-map.md`

### 目的

整理 cuPHYController YAML 的重要參數。

### 應該包含

* NIC / PCIe address
* O-RU MAC address
* VLAN
* fronthaul 相關設定
* L1 / PHY 相關設定
* compression
* eAxC mapping
* 和 Metanoia O-RU 需要對齊的項目

### 完成標準

能知道接 Metanoia O-RU 時，cuPHYController YAML 哪些欄位一定要改。

---

## `l2-l1-debug-checklist.md`

### 目的

建立 OAI L2+ 和 Aerial cuPHY 之間的 debug checklist。

### 應該包含

* OAI L2+ 是否啟動
* cuPHYController 是否啟動
* NVIPC 是否正常
* FAPI message 是否有交換
* slot timing 是否正常
* 常見錯誤與排查順序

### 完成標準

遇到 OAI 和 cuPHY 沒接起來時，可以用這份 checklist 分層檢查。

---

# 6. `internship-notes/metanoia-oru-prep/`

## `metanoia-hardware-profile.md`

### 目的

整理 Metanoia O-RU 硬體資訊。

### 應該包含

* 板子型號
* firmware version
* 支援 band
* 支援 bandwidth
* 支援 SCS
* TX / RX port
* RF chain
* 網路 port
* 電源與線路資訊

### 完成標準

能清楚知道手上的 Metanoia 板子硬體能力與限制。

---

## `metanoia-access-method.md`

### 目的

整理 Metanoia O-RU 的登入與管理方式。

### 應該包含

* M-plane IP
* 登入方式
* 帳號權限
* Web / SSH / NETCONF / vendor tool
* 如何查看狀態
* 如何修改設定
* 如何查看 log / alarm

### 完成標準

能獨立登入 Metanoia O-RU 並查看基本狀態。

---

## `metanoia-network-config.md`

### 目的

整理 Metanoia O-RU 的網路設定。

### 應該包含

* management IP
* C/U-plane MAC address
* VLAN ID
* switch port
* gNB server 對應 NIC
* MTU
* routing / interface 設定
* eCPRI 網路相關資訊

### 完成標準

能清楚對應 server、switch、Metanoia O-RU 之間的網路設定。

---

## `metanoia-ptp-config.md`

### 目的

整理 Metanoia O-RU 的 PTP 同步設定。

### 應該包含

* PTP profile
* PTP domain
* GrandMaster 設定
* switch PTP 設定
* O-RU lock status
* 查詢 lock 的方法
* PTP 失敗時的可能原因

### 完成標準

能確認 O-RU 是否 PTP lock，並知道 PTP 不正常時要查哪裡。

---

## `metanoia-rf-config.md`

### 目的

整理 Metanoia O-RU 的 RF 設定。

### 應該包含

* band
* center frequency
* ARFCN
* bandwidth
* SCS
* TDD pattern
* TX power
* RX gain
* antenna port
* 是否與 OAI / cuPHY 設定一致

### 完成標準

能確認 OAI、cuPHY、Metanoia O-RU 的 RF 相關參數是否對齊。

---

## `metanoia-ecpri-config.md`

### 目的

整理 Metanoia O-RU 的 eCPRI / fronthaul 設定。

### 應該包含

* eCPRI VLAN
* C-plane / U-plane 設定
* local / peer MAC
* UDP / eCPRI 設定
* fronthaul port
* packet capture 方法
* 常見錯誤

### 完成標準

能確認 cuPHY 到 Metanoia O-RU 的 fronthaul 封包設定是否正確。

---

## `metanoia-eaxc-mapping.md`

### 目的

整理 eAxC ID mapping。

### 應該包含

* DL eAxC ID
* UL eAxC ID
* PRACH eAxC ID
* antenna carrier 對應
* cuPHY 設定中的 eAxC
* O-RU 設定中的 eAxC
* mismatch 時可能造成的問題

### 完成標準

能確認 cuPHY 和 Metanoia O-RU 的 antenna carrier / eAxC ID 對應一致。

---

## `metanoia-compression-setting.md`

### 目的

整理 fronthaul IQ compression 設定。

### 應該包含

* compression mode
* bit width
* BFP / block floating point 設定
* cuPHY 支援的 compression
* Metanoia 支援的 compression
* mismatch 時可能造成的問題

### 完成標準

能確認 cuPHY 和 Metanoia O-RU 對 IQ compression 的設定一致。

---

## `metanoia-oru-readiness-checklist.md`

### 目的

建立接上 Metanoia O-RU 前的最後檢查表。

### 應該包含

* 硬體檢查
* 網路檢查
* PTP 檢查
* RF 設定檢查
* eCPRI 檢查
* eAxC 檢查
* compression 檢查
* OAI config 檢查
* cuPHY YAML 檢查

### 完成標準

所有項目確認後，才進入實際 bring-up。

---

# 7. `internship-notes/metanoia-integration/`

## `bringup-plan.md`

### 目的

規劃 Metanoia O-RU 實際 bring-up 的順序。

### 應該包含

* bring-up 目標
* 前置條件
* 啟動順序
* 每一步的成功條件
* 需要保存的 log
* 回復或 rollback 方法

### 完成標準

可以照這份文件一步一步啟動 Metanoia O-RU 整合流程。

---

## `bringup-daily-log.md`

### 目的

記錄每天 bring-up 做了什麼、結果如何、遇到什麼問題。

### 應該包含

* 日期
* 今日目標
* 執行步驟
* 結果
* log / screenshot
* 問題
* 明日計畫

### 完成標準

整合過程可追蹤，不會只靠記憶。

---

## `cuphycontroller-metanoia-yaml-notes.md`

### 目的

記錄為了接 Metanoia O-RU，cuPHYController YAML 做了哪些修改。

### 應該包含

* 原始設定
* 修改後設定
* 修改原因
* 對應 Metanoia O-RU 的哪個設定
* 測試結果
* 是否需要 rollback

### 完成標準

任何 YAML 修改都有理由與紀錄。

---

## `oai-gnb-metanoia-config-notes.md`

### 目的

記錄為了接 Metanoia O-RU，OAI gNB config 做了哪些修改。

### 應該包含

* PLMN
* TAC
* band
* ARFCN / frequency
* bandwidth
* SCS
* TDD pattern
* AMF / CN 相關設定
* 修改前後差異

### 完成標準

能清楚知道 OAI 端為 Metanoia O-RU 整合修改了哪些設定。

---

## `ptp-lock-test-result.md`

### 目的

記錄 PTP lock 測試結果。

### 應該包含

* GrandMaster 狀態
* switch PTP 設定
* O-RU PTP 狀態
* lock / unlock 結果
* 測試時間
* log 或截圖
* 問題與下一步

### 完成標準

能證明 O-RU 是否完成時間同步。

---

## `ecpri-connectivity-test.md`

### 目的

記錄 eCPRI / fronthaul connectivity 測試。

### 應該包含

* 測試目標
* server NIC
* switch port
* O-RU port
* VLAN
* MAC
* packet capture 結果
* 是否看到 eCPRI packet
* 問題與下一步

### 完成標準

能確認 cuPHY 到 Metanoia O-RU 的 fronthaul 封包是否有通。

---

## `oru-onair-check.md`

### 目的

記錄 O-RU 是否 on-air。

### 應該包含

* O-RU RF 狀態
* cell 是否發射
* UE 是否掃得到 cell
* 頻率 / band / SSB 設定
* O-RU log / alarm
* 結果與問題

### 完成標準

能確認 Metanoia O-RU 是否真的發射無線訊號。

---

## `ue-attach-test-result.md`

### 目的

記錄 UE attach 測試結果。

### 應該包含

* UE / SIM 資訊
* PLMN / APN
* 是否 detect cell
* 是否 RACH
* 是否 RRC connected
* 是否 NAS registration
* 是否 PDU session success
* OAI / cuPHY / CN log
* 失敗原因分析

### 完成標準

能清楚判斷 UE attach 成功或失敗在哪一層。

---

## `ping-test-result.md`

### 目的

記錄 ping 測試結果。

### 應該包含

* 測試方向
* UE IP
* target IP
* ping command
* 成功率
* latency
* 失敗原因
* 對應 log

### 完成標準

能確認 user plane 是否基本可用。

---

## `iperf-test-result.md`

### 目的

記錄 iperf throughput 測試結果。

### 應該包含

* 測試方向 DL / UL
* iperf server / client
* bandwidth
* throughput
* packet loss
* jitter
* 測試條件
* 可能瓶頸分析

### 完成標準

能初步評估 E2E data path 的 throughput。

---

## `integration-issue-list.md`

### 目的

整理整合過程中的所有問題。

### 應該包含

* 問題 ID
* 問題描述
* 影響層級
* 目前假設
* 已嘗試方法
* 下一步
* 狀態
* 負責人或需詢問對象

### 建議格式

| ID    | Issue       | Layer     | Current Guess      | Tried       | Next Action         | Status |
| ----- | ----------- | --------- | ------------------ | ----------- | ------------------- | ------ |
| I-001 | UE 看不到 cell | RF / O-RU | RF config mismatch | Checked PTP | Check SSB frequency | Open   |

### 完成標準

整合問題可以被追蹤、分類、回報，而不是散在對話或腦中。

---

# 8. `internship-notes/final-report/`

## `internship-final-summary.md`

### 目的

整理整個實習的最終總結。

### 應該包含

* 實習目標
* 完成事項
* 未完成事項
* 主要學習成果
* 主要技術成果
* 遇到的問題
* 後續建議

### 完成標準

可以作為最後對公司或老師的總結文件。

---

## `e2e-architecture-summary.md`

### 目的

整理最終版 E2E 架構理解。

### 應該包含

* 最終 E2E 架構圖
* 每個 component 的角色
* control plane
* user plane
* OTA 與 E2E 的關係
* 實際環境對應

### 完成標準

能完整說明 OAI L2+、Aerial cuPHY、Metanoia O-RU、UE、5GC 的關係。

---

## `reproduction-summary.md`

### 目的

整理學長實驗重現的最終結果。

### 應該包含

* 重現目標
* 重現環境
* 重現步驟
* 成功結果
* 失敗或差異
* baseline log
* 學到的重點

### 完成標準

公司能看出你不是只有照跑，而是有完整紀錄與理解。

---

## `metanoia-oru-integration-summary.md`

### 目的

整理 Metanoia O-RU 整合結果。

### 應該包含

* 整合目標
* 硬體與網路架構
* 設定對齊結果
* bring-up 結果
* OTA / attach / traffic 測試結果
* 遇到的問題
* 後續工作

### 完成標準

能清楚呈現 Metanoia O-RU 整合到哪一步。

---

## `config-mapping-summary.md`

### 目的

整理 OAI config、cuPHYController YAML、Metanoia O-RU 設定的總對照表。

### 應該包含

* OAI 參數
* cuPHY 參數
* Metanoia O-RU 參數
* 是否一致
* 修改紀錄
* 備註

### 建議格式

| Item | OAI Config | cuPHY YAML | Metanoia O-RU | Status    |
| ---- | ---------- | ---------- | ------------- | --------- |
| Band |            |            |               | Confirmed |
| SCS  |            |            |               | Pending   |
| VLAN |            |            |               | Confirmed |

### 完成標準

後續接手者可以直接用這份表確認三方設定是否一致。

---

## `test-result-summary.md`

### 目的

整理所有測試結果。

### 應該包含

* PTP test
* eCPRI test
* O-RU on-air test
* UE attach test
* ping test
* iperf test
* 每個測試的狀態與證據

### 完成標準

可以一眼看出哪些測試通過、哪些失敗、失敗在哪一層。

---

## `unresolved-issues.md`

### 目的

整理最後仍未解決的問題。

### 應該包含

* 問題描述
* 影響範圍
* 已嘗試方法
* 目前推測
* 需要誰協助
* 建議下一步
* 優先級

### 完成標準

不是只列問題，而是讓下一個人知道如何繼續處理。

---

## `debug-guide.md`

### 目的

整理整個實習過程累積出的 debug guide。

### 應該包含

* 分層 debug 流程
* 常見問題
* 對應 log
* 對應 config
* 建議檢查順序
* 真實案例

### 完成標準

後續遇到類似問題時，可以直接照這份 guide 排查。

---

## `next-step-recommendation.md`

### 目的

整理後續建議。

### 應該包含

* 短期建議
* 中期建議
* 長期建議
* 技術風險
* 優先順序
* 需要補的文件或資源

### 完成標準

公司或下一位接手者可以知道下一步最該做什麼。

---

# 9. `logs/`

## `2026-06.md`

### 目的

記錄 2026 年 6 月的每日進度。

### 應該包含

* 日期
* 今日目標
* 完成事項
* 遇到問題
* 明日計畫
* 相關文件連結

### 完成標準

可以回溯 6 月底做了哪些交接與背景準備。

---

## `2026-07.md`

### 目的

記錄 2026 年 7 月的每日進度。

### 應該包含

* E2E 架構理解
* 學長實驗重現
* command / config / log 整理
* OAI L2+ / cuPHY 學習
* 每日問題與進度

### 完成標準

可以回溯 7 月實習前半段如何從理解架構走到重現與介面學習。

---

## `2026-08.md`

### 目的

記錄 2026 年 8 月的每日進度。

### 應該包含

* Metanoia O-RU 準備
* bring-up
* PTP / eCPRI / OTA / UE attach / ping / iperf 測試
* 問題與解法
* final report 整理進度

### 完成標準

可以回溯 8 月 O-RU 整合與驗證過程。

---

# 11. `issues/`

## `open-questions.md`

### 目的

整理所有尚未確認的問題。

### 應該包含

* 問題
* 所屬主題
* 優先級
* 要問誰
* 狀態
* 回答紀錄

### 完成標準

所有疑問都有追蹤，不會遺漏。

---

## `technical-blockers.md`

### 目的

整理會阻擋進度的技術問題。

### 應該包含

* blocker 描述
* 影響範圍
* 卡住的原因
* 已嘗試方法
* 需要的協助
* 下一步
* 狀態

### 完成標準

可以清楚回報目前真正擋住進度的是什麼。

---

## `questions-for-company.md`

### 目的

整理需要問公司的問題。

### 應該包含

* 問題
* 為什麼需要問
* 影響哪個階段
* 優先級
* 公司回覆
* 後續 action

### 完成標準

與公司討論時可以直接照這份文件問，不會臨時漏掉重點。

