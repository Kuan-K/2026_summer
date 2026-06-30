# aerial-cuphy-basic-role

> Reference :
> 
>   https://docs.nvidia.com/aerial/cuda-accelerated-ran/latest/index.html
> 
>   https://docs.nvidia.com/aerial/cuda-accelerated-ran/latest/cubb/cuphy_developer_guide/index.html
>
>   https://docs.nvidia.com/aerial/cuda-accelerated-ran/latest/cubb/cuphy_developer_guide/cuphy_software_arch_overview.html
>
>   https://docs.nvidia.com/aerial/cuda-accelerated-ran/latest/cubb/cuphy_developer_guide/cuphy_components.html


## Topic 
1. What is Aerial CUDA-Accelerated RAN
2. What is Aerial cuPHY
3. cuPHY architecture
4. Introduction to each component
5. Glossary


## What is Aerial CUDA-Accelerated RAN

Aerial CUDA-Accelerated RAN 是一種 SDK，用來把 5G/6G 基地台裡面很吃運算的 RAN / gNB 軟體，放到 NVIDIA GPU 加速平台上執行。

## What is Aerial cuPHY

Aerial cuPHY 是 Aerial CUDA-Accelerated RAN 中負責 L1/PHY layer 訊號處理的，主要對應 O-RAN 7.2x split 架構中的 upper PHY 部分。將PHY layer 複雜的運算放在GPU上做平行運算，但主要的控制信號還是由CPU處理；cuPHY 內包含cuPHY controller, L2 Adapter, cuPHY Driver, cuPHY Channel pipelines。

## cuPHY architecture

從L2下來的FAPI message 與 TB data 都會經過 nvIPC 後到L1，L2的訊息分成兩種 1. FAPI 夾帶著控制訊號(用來描述控制、排程、slot 配置、MCS等資訊)與TB data的資訊(資料大小)、與 2. TB data 真正要傳送的使用者資料

FAPI message 會經過L2 Adapter 將FAPI commands轉成slot command 讓cuPHY Driver 能看懂；cuPHY Driver 作為cuPHY的控制中心會分配GPU等資源，讓cuPHY pipeline Channel 可以去做計算，cuPHY Channel pipelines 能將TB data轉為實際要發送的IQ data 並存放在GPU memory內。

C-plane 從cuPHY Driver 下來後會經過FH library 後再通過DPDK進入BF-3 而U-plane則是直接從GPU memory 拿取資料後經過BF-3 最後由RU發射。上行的部分RU接收後資料會直接進入GPU memory內做處理，這時cuPHY Channel pipelines的工作是將IQ data轉為 TB data

<img width="960" height="720" alt="cuphy_sw_stack" src="https://github.com/user-attachments/assets/3b7a04fb-750a-4b17-b938-56a971e743f3" />

[quote from NVIDIA](https://docs.nvidia.com/aerial/cuda-accelerated-ran/latest/cubb/cuphy_developer_guide/cuphy_software_arch_overview.html)


## Introduction to each component

### L2 Adapter

L2 Adapter 在 L2 與 L1 之間， MAC 層透過 SCF FAPI 傳送控制訊號，L2 Adapter 將這些SCF FAPI commands 轉為 slot commands ，會告訴L1資訊(這個 slot 要做什麼、要處理哪個 UE、使用哪些 RB、用什麼 MCS、是 DL 還是 UL)；L2 Adapter 會追蹤 slot timing，如果 L2 的訊息太晚到，可能直接丟棄。


### cuPHY Driver

cuPHY Driver 是控制中心，負責根據 L2 Adapter 轉換後的 slot commands，呼叫GPU 上的 CUDA kernel做訊號處理，同時也負責管理FH Library 與 BF3 之間的溝通。並且會回傳L1處理的結果告訴L2
* CRC indication:上行資料解碼成功還是失敗
* UCI indication:手機上行傳回來的控制資訊(HARQ ACK / NACK, CQI)
* Measurement reports:量測結果(接收功率、通道品質等)

### FH Driver Library

FH Driver Library 是為了確保 O-RU 與 O-DU 之間能準時發送與接收
* C-plane 的控制信號經過DPDK傳入BF-3，用來告訴 O-RU 某個時間要如何處理資料。
* U-plane 的資料訊號分上下行
  * DL: DL 的 IQ data 從GPU 的 Memory 直接送往BF-3
  * UL: UL 的 packets 從 O-RU 進來後，可以直接複製到 GPU memory

<img width="827" height="583" alt="flow_of_packets_on_fh" src="https://github.com/user-attachments/assets/5f377d3e-ddd5-4551-9223-f6e2c15dd1c1" />

[note]

DPDK:可先理解成一套高速封包處理工具，讓 CPU 可以更有效率地直接處理網路封包。

### BF3

BF3 = NVIDIA BlueField-3 ， 一種 NVIDIA 的高階 NIC 

NIC = Network Interface Card，網路介面卡，O-RAN / 5G fronthaul 裡，負責 fronthaul 封包進出與時間排程。

BF3，除了收發封包，也能做一些加速、封包處理、資料搬移、時間同步等工作，是資料進出 O-RU 的硬體。

### cuPHY Controller

cuPHY controller 是cuPHY啟動時的主控程式，負責根據YAML設定檔，初始化整個L1系統，建立資源、啟動物件讓整個cuPHY系統可以開始運作

## Glossary 

| 名詞      | 簡單定義                  | 在 cuPHY 架構中的角色                 |
| ------- | --------------------- | ------------------------------ |
| FAPI    | L2 / L1 介面標準       | 定義 L2 和 L1 如何交換控制、排程與資料相關訊息    |
| nVIPC   | NVIDIA IPC 通道        | L2 和 L1 之間實際承載訊息的通道       |
| TB data | Transport Block data  | L2 和 L1 之間交換的使用者資料           |
| IQ data | I/Q sample data       | O-DU 和 O-RU 之間傳輸的 PHY 取樣資料     |
| C-plane | Control plane         | 控制如何處理資料                 |
| U-plane | User plane            | 實際要傳輸的資料                  |
| BF3     | BlueField-3 NIC       | O-DU 和 O-RU 之間的的 O-RAN fronthaul 封包收發與資料搬移|

