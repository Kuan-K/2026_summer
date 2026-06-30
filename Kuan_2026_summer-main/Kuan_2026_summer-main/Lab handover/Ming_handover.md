# Ming Handover

## topic

  1. tool and labserver
  2. nFAPI and Monolithic gNB
  3. to do

## tool and labserver

* AnyDesk (遠端桌面) : 用來控制實驗室的手機

  實驗室有一台三星與一台商用手機 

* wireGuard (VPN) : 用來直接連到實驗室server

  與學長要VPN 檔連進去就可以

[note]
alt+shift+d 可以切分 cmd

## nFAPI and Monolithic gNB

nFAPI : MAC層 以及PHY層之間呢主要是透過FAPI 訊息格式做溝通，那麼如果要將FAPI 拆分成兩台機器的話呢就需要使用 nFAPI 透過網路的方式拆分成不同機器去部屬，option 6 split 的時候，我們會稱MAC層以上的叫做VNF PHY層以下的叫做PNF

E2E 步驟先連線至實驗室server

```
ssh hpe@192.168.8.26

#開啟 VMF
sudo -E NFAPI_TRACE_LEVEL=info \numactl --cpunodebind=1 --membind=1 \taskset -c 8-15,40-47 ./nr-softmodem -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb-vnf-split.sa.band78.273prb.nfapi-hpe.conf --nfapi VNF 2>&1 | tee ~/gNB-logs/vnf-hpe-ming.log

#開啟 PNF
ssh oai72_su@192.168.8.82
sudo NFAPI_TRACE_LEVEL=info ./nr-softmodem -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb-pnf-split.sa.band78.fhi72.nfapi.4x4-pegatron-hpe.conf  --nfapi PNF --thread-pool 8,9,10,11,12,14,15,1 2>&1 | tee ~/gNB-logs/pnf-hpe-ming.log
```

Monolithic : 不將gNB拆分，整個跑，所以沒有 VNF 與 PNF

[note]
打iperf 時 Doｗnlink throughput 需要看UE端

## to do
試著重現Ming的論文實驗與環境

完成實驗五，並輸出結果圖

查看 sourse code 作筆記

