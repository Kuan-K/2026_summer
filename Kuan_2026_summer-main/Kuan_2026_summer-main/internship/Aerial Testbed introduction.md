# Aerial Testbed study note

> Reference :
> 
>   https://docs.nvidia.com/aerial/testbed/latest/text/product_description/index.html
>
>   https://docs.nvidia.com/aerial/testbed/latest/text/installation_guide/manual_install.html

## Topic
  1.  [architecture](#architecture)
  2.  [Key Features and Specifications](#Key-Features-and-Specifications)

## architecture

<img width="1135" height="1153" alt="E2E 架構" src="https://github.com/user-attachments/assets/06ee52b0-a39a-417d-adb5-1af5f5a2d6ab" />


## Key Features and Specifications


| Feature                                | Value                                                             | Note |
| -------------------------------------- | ----------------------------------------------------------------- | ---- |
| Number Antennas                        | 4T4R                                                              |天線數量 4個讀取4個接收      |
| Number of Component Carriers           | 1x 100MHz carrier                                                 |只使用一個 100 MHz 頻寬      |
| Subcarrier Spacing (PDxCH; PUxCH, SSB) | 30 kHz                                                            |SCS = 30k 一個 slot =0.5ms      |
| FFT Size                               | 4096                                                              |OFDM 訊號在時域與頻域轉換時一次處理 4096 個取樣點      |
| MIMO layers                            | DL: 4 layers; UL: 1 layer                                         |基地台可以同時用多個資料流傳資料給 UE ，UE 上傳方向只支援 1 條主要資料流     |
| Duplex Mode                            | Release 15 SA TDD                                                 |TDD:上下行使用同一個頻段，但用不同時間切換  |
| Number of RRC connected UEs            | Up to 100                                                         |可以被基地台管理與排程的 UE數量   |
| Number of UEs/TTI                      | 16                                                                |每一個傳輸時間間隔內，最多可以排程 16 台 UE 傳輸資料    |
| Frame structure and slot format        | DDDDDDSUUU<br>DSUUU                                               |D:下行 U:上行 S:特殊(上下行都可以)      |
| User plane latency (RRC connected)     | < 10ms one way for DL and UL mode                                 |單向資料延遲都小於 10 ms      |
| Synchronization and Timing             | IEEE 1588v2 PTP; SyncE; LLS-C3                                    |PTP 比較偏向時間同步，SyncE 比較偏向頻率同步     |
| Frequency Band                         | n78, n48 (CBRS)                                                   |n78 :常見的 5G sub-6 GHz 頻段，大約在 3.3 GHz 到 3.8 GHz 附近      |
| Max Transmit Power                     | 22 dBm at RF connector                                            |RF 接頭端量到的最大輸出功率是 22 dBm      |
| Peak throughput                        | Refer to the Release Notes for the latest peak throughput values. |峰值吞吐量會隨版本更新而改變      |
| Bi-directional UDP Traffic             | > 10+ hours exercised (SMC-GH)                                    |系統有做長時間穩定性驗證 > 10 hours      |
