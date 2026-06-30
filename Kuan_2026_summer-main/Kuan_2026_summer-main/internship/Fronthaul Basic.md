# O-RAN Fronthaul study note

## Topic
1. Fronthaul 在 O-RAN 架構中的位置
2. 為什麼不能把 O-RU 當成一般網路設備
3. eCPRI 是什麼
4. C-plane / U-plane / S-plane / M-plane
5. VLAN / MAC / Ethernet 為什麼重要
6. PTP 為什麼重要


## 1. Fronthaul 在 O-RAN 架構中的位置

  fornthaul 是在 O-DU 與 O-RU 之間，以O-RAN 常用的 7.2x split，就會切在High PHY 與 low PHY 之間，常用fronthaul switch 來實現。

## 2. 為什麼不能把 fornthaul 當成一般網路連接

  因為切分得位置在實體層，一般網路設備收到封包晚一點，可能只是網頁慢一點。O-RU 收到資料晚一點、時間對不上，結果可能是：
```
UE 收不到基地台訊號
UE decode 失敗
random access 失敗
```
重點不是在能不能送封包，而是封包送到以後，O-RU 能不能在正確時間、正確頻率、正確天線上發射。

所以fornthaul 也需要嚴格的規格定義

| 要解決的問題 | 對應規格 / 機制 | 主要用途 |
|---|---|---|
| 資料怎麼包 | eCPRI | 定義 fronthaul 封包格式，讓 O-DU / cuPHY 和 O-RU 能用 Ethernet 傳送即時資料 |
| 控制怎麼下 | C-plane | 傳送控制資訊，告訴 O-RU 哪個時間、頻率，要怎麼處理 |
| IQ data  | U-plane | 傳送實際 IQ sample data，也就是 O-RU 要發射或接收的基頻資料 |
| 時間怎麼同步 | S-plane / PTP | 讓 O-DU / cuPHY 和 O-RU 對齊 frame、slot、symbol timing |
| 設備怎麼設定 | M-plane | 管理與設定 O-RU |
| 封包怎麼轉送 | Ethernet / VLAN / MAC / QoS | 確保 eCPRI 封包能送到正確 O-RU，並具備正確分類、優先權與傳輸條件 |
| RF 怎麼對應 | band / SCS / bandwidth | 確保 O-DU / cuPHY 算出的資料能對應到正確頻段、頻寬、天線|


## 3. eCPRI 是什麼
- eCPRI 與傳統 CPRI 差異
- eCPRI packet 的用途
- O-RAN C-plane / U-plane 如何透過 eCPRI 傳輸

## 4. C-plane / U-plane / S-plane / M-plane
| Plane | 我目前的理解 | 在 fronthaul 中的功能 | 如果沒處理好可能會怎樣 |
|---|---|---|---|
| C-plane | 控制 O-RU 要怎麼使用無線資源 | 例如控制 beam、resource mapping，告訴 O-RU 哪個時間/頻率資源要怎麼處理 | O-RU 可能不知道 IQ data 要對應到哪個 radio resource |
| U-plane | 傳實際的基頻資料 | 傳送 IQ sample data，這些資料最後會被 O-RU 轉成 RF 訊號，或從 RF 接收後送回 O-DU | 封包可能有到，但資料內容或格式錯會導致 RF 訊號錯誤 |
| S-plane | 讓兩邊時間/頻率同步 | 例如 PTP / SyncE，讓 O-DU 和 O-RU 對齊 frame、slot、symbol timing | 即使資料有送到，也可能在錯誤時間發射或接收，或是無法發射 |
| M-plane | 設定與管理 O-RU | 設定 O-RU、查詢 RU 資訊 | O-RU 可能沒有被正確初始化或設定，導致後面的無法正常工作 |
## 5. VLAN / MAC / Ethernet 為什麼重要
- O-RU 和 cuPHY 必須知道彼此 MAC address
- VLAN ID 要一致
- PCP / priority 影響 fronthaul 封包優先權
- MTU / jumbo frame 可能影響 IQ data 傳輸

## 6. PTP 為什麼重要
- O-RU 和 O-DU 必須在時間上同步
- PTP Grandmaster / slave clock
- 如果同步失敗，RF 收發 timing 會錯

## 7. cuPHY 與 Metanoia O-RU 需要對齊的設定表
