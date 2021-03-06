---
title: "自動調整的最佳做法 | Microsoft Docs"
description: "在 Azure 中自動調整 Web 應用程式、虛擬機器擴展集和雲端服務的規模模式。"
author: anirudhcavale
manager: orenr
editor: 
services: monitoring-and-diagnostics
documentationcenter: monitoring-and-diagnostics
ms.assetid: 9fa2b94b-dfa5-4106-96ff-74fd1fba4657
ms.service: monitoring-and-diagnostics
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/07/2017
ms.author: ancav
ms.translationtype: HT
ms.sourcegitcommit: cddb80997d29267db6873373e0a8609d54dd1576
ms.openlocfilehash: 54dad831287376db7fb2dc46e4591be1499dc072
ms.contentlocale: zh-tw
ms.lasthandoff: 07/18/2017

---
# <a name="best-practices-for-autoscale"></a>自動調整規模的最佳做法
本文會說明在 Azure 中自動調整的最佳做法。 Azure 監視器自動調整僅適用於[虛擬機器擴展集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、[雲端服務](https://azure.microsoft.com/services/cloud-services/)和 [App Service - Web Apps](https://azure.microsoft.com/services/app-service/web/)。 其他 Azure 服務使用不同的調整方法。

## <a name="autoscale-concepts"></a>自動調整的概念
* 資源可以只有「一項」  自動調整設定。
* 自動調整設定可有一或多個設定檔，而且每個設定檔都能有一或多項自動調整規則。
* 自動調整設定會水平調整執行個體，其中「相應放大」為增加執行個體數量，而「相應縮小」則是減少執行個體數量。
  自動調整設定可設定執行個體數的最大值、最小值及預設值。
* 自動調整作業一律會讀取相關聯的度量作為調整依據，據此檢查其是否超過設定的臨界值，以執行相應放大或相應縮小。 您可以在 [Azure 監視器自動調整的常見度量](insights-autoscale-common-metrics.md)中，檢視自動調整據以調整的度量清單。
* 所有臨界值都是在執行個體層級計算。 例如，「當執行個體計數為 2 時，若平均 CPU > 80% ，即相應放大 1 個執行個體」表示當所有執行個體的平均 CPU 大於 80% 時即相應放大。
* 您一律會從電子郵件收到失敗通知。 具體而言，目標資源的擁有者、參與者與讀者都會收到電子郵件。 當自動調整從失敗復原並開始正常運作時，您也一律會收到「復原」電子郵件。
* 您可以選擇從電子郵件及 Webhook 接收調整動作成功的通知。

## <a name="autoscale-best-practices"></a>自動調整最佳做法
使用自動調整時，請使用下列最佳做法。

### <a name="ensure-the-maximum-and-minimum-values-are-different-and-have-an-adequate-margin-between-them"></a>確定最大值與最小值不同，而且兩者之間有差距適當。
若設定的最小值等於 2，而最大值也等於 2，且目前執行個體計數為 2，將不會有任何調整動作。 在執行個體計數的最大值與最小值之間 (含這兩個值)，需保留適當的差距。 在這些限制之間，一定律會自動調整。

### <a name="manual-scaling-is-reset-by-autoscale-min-and-max"></a>自動調整的最小值與最大值會重設手動調整
如果您手動將執行個體計數的值更新為高於最大值或低於最小值，自動調整引擎會自動調整回最小值 (如果低於) 或最大值 (如果高於)。 例如，您設定的範圍是 3 到 6。 如果您有一個執行執行個體正在執行，自動調整引擎會在它下次執行時調整為 3 個執行個體。 同樣地，它會將 8 個執行個體，在下次執行時相應縮小至 6 個。  手動調整是暫時的，除非您也同時重設自動調整規則。

### <a name="always-use-a-scale-out-and-scale-in-rule-combination-that-performs-an-increase-and-decrease"></a>請一律使用相應放大和相應縮小規則的組合來執行增加與減少。
若您只使用組合中的其中一部分，則自動調整只會相應放大或縮小該單邊，直到達到最大值或最小值為止。

### <a name="do-not-switch-between-the-azure-portal-and-the-azure-classic-portal-when-managing-autoscale"></a>管理自動調整時，請勿切換使用 Azure 入口網站與 Azure 傳統入口網站。
若是雲端服務及應用程式服務 (Web Apps)，請使用 Azure 入口網站 (portal.azure.com) 建立及管理自動調整設定。 若是虛擬機器擴展集，請使用 PowerShell、CLI 或 REST API 建立及管理自動調整設定。 管理自動調整設定時，請勿切換使用 Azure 傳統入口網站 (manage.windowsazure.com) 與 Azure 入口網站 (portal.azure.com)。 Azure 傳統入口網站及其基礎後端有其限制。 請使用 Azure 入口網站的圖形化使用者介面來管理自動調整。 此外也可選擇使用自動調整 PowerShell、CLI 或 REST API (透過 Azure 資源總管)。

### <a name="choose-the-appropriate-statistic-for-your-diagnostics-metric"></a>為您的診斷度量選擇適當的統計資料
針對診斷度量，您可以選擇 [平均值]、[最小值]、[最大值] 和 [總計] 作為據以調整的度量。 最常用的統計資料是 [平均值] 。

### <a name="choose-the-thresholds-carefully-for-all-metric-types"></a>請小心選擇所有度量類型的臨界值
建議您根據實際情況，小心選擇不同的相應放大與相應縮小臨界值。

「不建議使用」  自動調整設定，例如下列範例中，將放大及縮小的臨界值設為相同的值或極類似的值：

* 當執行緒計數 <= 600 時，增加 1 個執行個體
* 當執行緒計數 >= 600 時，減少 1 個執行個體

下列範例顯示可能會導致行為混淆的設定。 考量以下發生順序。

1. 假設一開始只有 2 個執行個體，之後每個執行個體的平均執行緒數成長為 625。
2. 自動調整會隨之相應放大，加入第 3 個執行個體。
3. 假設接下來執行個體的平均執行緒計數降至 575，
4. 則在相應減少之前，自動調整會嘗試評估相應縮小後的最終狀態。 例如，575 x 3 (目前的執行個體計數) = 1,725 / 2 (相應減少後的最終執行個體數) = 862.5 個執行緒。 這表示即便平均執行緒計數維持不變，或甚至降至極少量，自動調整仍須在相應縮小之後立即再相應放大。 但自動調整若再相應增加，整個程序將會重複執行，進行產生無限迴圈。
5. 為了避免這種「不穩定」的狀況，自動調整根本不會相應減少， 而會在下次執行服務的工作時略過並重新評估條件。 這可能會讓許多人困惑不已，因為當平均執行緒計數達到 575 時，自動調整完全不運作。

相應縮小期間的估計是為了避免「不穩定」情況 (持續地反覆相應縮小和相應放大動作)。 當您為相應放大及相應縮小選擇相同的臨界值時，請注意這項行為。

建議您在選擇相應放大及相應縮小的臨界值時，為兩者之間保留適當的差距。 例如您可以考慮下列比較適當的規則組合。

* 當 CPU% >= 80 時，增加 1 個執行個體
* 當 CPU% <= 60 時，減少 1 個執行個體

在此案例中  

1. 假設一開始只有 2 個執行個體，
2. 當執行個體的平均 CPU% 達到 80 時，自動調整會隨之相應放大，加入第 3 個執行個體。
3. 假設 CPU% 在經過一段時間後降至 60。
4. 自動調整的相應縮小規會先評估相應縮小之後的最終狀態。 例如 60x3 (目前的執行個體計數) = 180/2 (相應減少時的最終執行個體數) = 90。 因為自動調整必須再於相應減少之後隨即相應放大，所以其不會相應縮小， 而會略過相應減少。
5. 下一次自動調整檢查，CPU 會繼續歸類為 50。 再次進行評估：50 x 3 個執行個體 = 150/2 個執行個體 = 75 (低於相應放大臨界值 80)，所以會依設定相應放大到 2 個執行個體。

### <a name="considerations-for-scaling-threshold-values-for-special-metrics"></a>調整特殊度量之臨界值時的注意事項
 對於特殊度量 (例如儲存體或服務匯流排佇列長度度量)，臨界值目前執行個體數所能使用的平均訊息數。 請謹慎選擇此度量的臨界值。

現在讓我們利用下列範例為您說明，讓您對此行為有更深入的了解。

* 當儲存體佇列訊息計數 >= 50 時，增加 1 個執行個體
* 當儲存體佇列訊息計數 <= 10 時，減少 1 個執行個體

考量以下發生順序：

1. 有 2 個儲存體佇列執行個體。
2. 隨著訊息不斷傳入，當您檢閱儲存體佇列時，訊息計數達到 50。 您可能認為自動調整應執行相應放大動作。 但請注意，自動調整仍然是每個執行個體 50/2 =  25 則訊息， 因此不會進行相應放大。 若要執行第一次相應放大，儲存體佇列中的總訊息計數應達到 100。
3. 當總訊息計數達到 100 時，
4. 就會執行相應放大動作而加入第 3 個儲存體執行個體。  除非佇列中的總訊息計數達到 150 (因為 150/3=50)，否則不會執行下一個相應放大動作。
5. 現在，佇列中的估計訊息數目便會變小。 若有 3 個執行個體，當所有佇列中的總訊息數相加達到 30 時，會執行第一次相應縮小動作，意即臨界值是每個執行個體的規模為 30/3 = 10 則訊息。

### <a name="considerations-for-scaling-when-multiple-profiles-are-configured-in-an-autoscale-setting"></a>當自動調整設定中設有多個設定檔時的調整注意事項
您可以在自動調整設定中選擇預設設定檔 (當沒有任何項目取決於排程或時間時套用)，也可以選擇週期性設定檔或期間固定的設定檔 (設有日期與時間範圍)。

當自動調整服務在處理這些設定時，一律會依下列順序進行檢查︰

1. 固定日期設定檔
2. 週期性設定檔
3. 預設 (一律) 設定檔

若符合設定檔條件，自動調整將不再檢查接下來的下一項設定檔條件。 自動調整一次只會處理一個設定檔。 這表示若您想要加入低層設定檔中的處理條件，也必須同時將這些規則加入目前的設定檔中。

請參考下列示範範例︰

下圖顯示的自動調整設定中，其預設設定檔的最小執行個體數 = 2，最大執行個體數 = 10。 此範例將規則設定成當佇列中的訊息計數大於 10 時執行相應放大，當佇列中的訊息計數小於 3 時執行相應縮小。 因此我們現在可以將資源調整為 2 到 10 個執行個體。

此外，星期一設定成使用週期性設定檔， 其中最小執行個體數 = 2，最大執行個體數 = 12。 這表示在星期一時，自動調整會在第一次檢查此條件；當執行個體計數為 2 時，會將其調整為新的最小值 3。 只要自動調整持續比對此設定檔條件 (星期一)，其便只會按照此設定檔中設定的規則，依據 CPU 執行相應放大/縮小。 此時不會檢查佇列長度。 若您也想要檢查佇列長度條件，應一併將預設設定檔中的這些規則加入星期一設定檔中。

當自動調整切換回預設設定檔時，同樣也會先檢是否符合最大值與最小值條件。 若當時的執行個體數為 12，將會相應縮小為 10 (預設設定檔允許的最大值)。

![自動調整設定](./media/insights-autoscale-best-practices/insights-autoscale-best-practices-2.png)

### <a name="considerations-for-scaling-when-multiple-rules-are-configured-in-a-profile"></a>當設定檔中設有多項規則時的調整注意事項
有些情況可能需要您在設定檔中設定多項規則。 當設定多項規則時，服務會使用下列自動調整規則集。

對於「相應放大」，自動調整會在符合任何規則時執行。
對於「相應縮小」，自動調整會要求必須符合所有規則。

現在我們以您有下列 4 項自動調整規則加以示範說明︰

* 當 CPU < 30% 時相應縮小 1
* 當記憶體 < 50% 時相應縮小 1​
* 當 CPU > 75% 時相應放大 1
* 當記憶體 > 75% 時相應放大 1​

接著會發生下列狀況：

* 當 CPU 為 76%，記憶體為 50% 時，會相應放大。
* 當 CPU 為 50%，記憶體為 76% 時，會相應放大。

反之，當 CPU 為 25%，記憶體為 51% 時，自動調整「不會」相應縮小。 若要相應縮小，CPU 必須達到 29%，而記憶體必須達到 49%。

### <a name="always-select-a-safe-default-instance-count"></a>請一律選取安全的預設執行個體計數
預設執行個體計數十分重要，在沒有度量可用時，自動調整會依據其計數調整服務。 因此，請選取對您工作負載而言最安全的預設執行個體計數。

### <a name="configure-autoscale-notifications"></a>設定自動調整通知
當發生下列情況時，自動調整傳送電子郵件，通知資源的系統管理員與參與者︰

* 自動調整服務無法採取動作。
* 自動調整服務無法使用度量決定規模。
* 度量恢復使用 (復原)，可用以決定規模。
  除了上述條件之外，您也可以設定電子郵件或 Webhook 通知，在調整動作成功時收到通知。
  
您也可以使用活動記錄警示來監視自動調整引擎的健康狀態。 以下範例為[建立活動記錄警示以監視訂用帳戶的所有自動調整引擎作業](https://github.com/Azure/azure-quickstart-templates/tree/master/monitor-autoscale-alert)，或[建立活動記錄警示以監視訂用帳戶中所有失敗的相應縮小/相應放大自動調整作業](https://github.com/Azure/azure-quickstart-templates/tree/master/monitor-autoscale-failed-alert)。

## <a name="next-steps"></a>後續步驟
- [建立活動記錄警示以監視訂用帳戶的所有自動調整引擎作業。](https://github.com/Azure/azure-quickstart-templates/tree/master/monitor-autoscale-alert)
- [建立活動記錄警示以監視訂用帳戶中所有失敗的相應縮小/相應放大自動調整作業](https://github.com/Azure/azure-quickstart-templates/tree/master/monitor-autoscale-failed-alert)

