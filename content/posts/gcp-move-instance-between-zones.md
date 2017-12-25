---
title: "[GCP] 將 VM 搬移至另一個 Zone"
date: 2017-12-25T19:16:35+08:00
---

GCP 的 Compute Engine 在開虛擬機的時候，需要同時選擇虛擬機所在的機房（Region）及子區域（Zone），一般來說在虛擬機建立時，選好 Region 及 Zone 之後，就不能再更換或搬家，只能刪掉重建，不過 gcloud 指令提供了換 Zone 的功能，讓這件事情變得很簡單，只需要一行指令：

	gcloud compute instances move example-instance --zone us-central1-a --destination-zone us-central1-f

上面的範例，即可把 `example-instance` 這台 VM 從 `us-central1-a` 搬到 `us-central1-f`。

整個搬遷的過程需要點時間，在過程間 GCP 控制界面上並不會有防呆機制，因此千萬不要在這過程中修改任何相關的設定或資源，以免搬遷過程失敗。

另外需要注意，該虛擬機必須要在「開機」的狀態下才能用，如果是關機狀態，會出現

	ERROR: (gcloud.compute.instances.move) Instance cannot be moved while in state: TERMINATED

也就是說，要先把這台虛擬機開機，才能使用 gcloud compute instances move 指令搬機器。

--

指令簡單歸簡單，深入研究可以發現，這個指令其實只是把一連串固定的操作全部整合成一個指令而已。GCP 也提供了全手動的方式幫機器搬家，整個操作步驟大約就是關閉關機後自動刪除硬碟功能、將硬碟建立 snapshot、刪除舊虛擬機、以 snapshot 在指定的 Zone 建立新虛擬機、開機，步驟有點複雜，有興趣可以翻閱參考連結的第一個，裡面有詳盡的步驟。

最後就是換 Region，理論上可以辦得到，但一直出現

	ERROR: (gcloud.compute.instances.move) Instances belonging to subnetworks cannot be moved interregionally.

應該是跟虛擬機的網路設定有關，就沒有深入研究要怎麼解決，目前看起來如果需要跨 Region 搬遷虛擬機，可能只能根據文件上的步驟手動搬遷了。


### Reference

* [Moving an Instance Between Zones](https://cloud.google.com/compute/docs/instances/moving-instance-across-zones)
* [gcloud compute instances move](https://cloud.google.com/sdk/gcloud/reference/compute/instances/move)
