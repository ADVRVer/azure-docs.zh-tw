---
title: "設定 OMS Log Analytics 中的資料來源 | Microsoft Docs"
description: "資料來源可定義 Log Analytics 要從代理程式和其他已連接的來源收集哪些資料。  本文說明 Log Analytics 如何使用資料來源的概念、詳細說明如何設定資料來源，並提供可用的不同資料來源的摘要。"
services: log-analytics
documentationcenter: 
author: bwren
manager: carmonm
editor: tysonn
ms.assetid: 67710115-c861-40f8-a377-57c7fa6909b4
ms.service: log-analytics
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 05/23/2017
ms.author: bwren
ms.translationtype: Human Translation
ms.sourcegitcommit: a30a90682948b657fb31dd14101172282988cbf0
ms.openlocfilehash: 00d030a502cf70ea9a5dea767f560cdf2919573e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/25/2017


---
# <a name="data-sources-in-log-analytics"></a>Log Analytics 中的資料來源
Log Analytics 會從 OMS 工作區的 [連接的來源] 收集資料，並將它儲存在 OMS 儲存機制中。  而您設定的資料來源可定義要從每個來源收集哪些資料。  OMS 儲存機制中的資料會以記錄組的形式儲存。  每個資料來源都會建立特定類型的記錄，每種類型各有自己的一組屬性。

![Log Analytics 資料收集](./media/log-analytics-data-sources/overview.png)

資料來源與 OMS 方案不同，後者也會從 [連接的來源] 收集資料，並在 OMS 儲存機制中建立記錄。  您可從方案庫將方案加入工作區；方案通常也會在 OMS 入口網站中提供其他的分析工具。  

## <a name="summary-of-data-sources"></a>資料來源的摘要
下表列出 Log Analytics 中目前可用的資料來源。  每個資料來源都有個別的文章連結，提供該資料來源的詳細資料。

| 資料來源 | 事件類型 | 說明 |
|:--- |:--- |:--- |
| [自訂的記錄檔](log-analytics-data-sources-custom-logs.md) |\<LogName\>_CL |Windows 或 Linux 代理程式上包含記錄資訊的文字檔。 |
| [Windows 事件記錄檔](log-analytics-data-sources-windows-events.md) |Event |Windows 電腦上從事件記錄檔收集的事件。 |
| [Windows 效能計數器](log-analytics-data-sources-performance-counters.md) |Perf |從 Windows 電腦收集的效能計數器。 |
| [Linux 效能計數器](log-analytics-data-sources-performance-counters.md) |Perf |從 Linux 電腦收集的效能計數器。 |
| [IIS 記錄檔](log-analytics-data-sources-iis-logs.md) |W3CIISLog |W3C 格式的網際網路資訊服務記錄檔。 |
| [Syslog](log-analytics-data-sources-syslog.md) |syslog |Windows 或 Linux 電腦上的 Syslog 事件。 |

## <a name="configuring-data-sources"></a>設定資料來源
您可以從 Log Analytics [設定] 中的 [資料] 功能表來設定資料來源。  系統會將任何設定傳遞到 OMS 工作區中所有已連接的來源。  您目前無法透過這項組態來排除任何代理程式。

![設定 Windows 事件](./media/log-analytics-data-sources/configure-events.png)

1. 在 OMS 主控台中，按一下畫面頂端的 [設定] 磚或 [設定] 按鈕。
2. 選取 [資料] 。
3. 按一下要設定的資料來源。
4. 參閱上表中每個資料來源的文件連結，即可取得其組態的詳細資訊。

> [!NOTE]
> 您目前無法在 Azure 入口網站中設定 Log Analytics 資料來源。

## <a name="data-collection"></a>資料收集
系統會在幾分鐘內，將資料來源組態傳遞給直接連接到 Log Analytics 的代理程式。  系統會從代理程式收集指定的資料，並依據每個資料來源特定的時間間隔，直接傳遞給 Log Analytics。  請參閱每個資料來源的文件，以了解這些特性。

若是已連接管理群組中的 System Center Operations Manager (SCOM) 代理程式，系統會將資料來源組態轉譯為管理組件，並依預設每隔 5 分鐘傳遞給管理群組。  如同其他任何代理程式一樣，此代理程式也會下載管理組件，並收集指定的資料。 視資料來源而定，資料會傳送至管理伺服器，而管理伺服器再將資料轉送至 Log Analytics，或者，由這個代理程式直接將資料傳送至 Log Analytics，而沒有經過管理伺服器。 如需詳細資訊，請參閱 [OMS 功能和方案的資料收集詳細資料](log-analytics-add-solutions.md#data-collection-details)。  您可以閱讀連接 SCOM 與 OMS 的詳細資訊，以及修改在 [設定與 System Center Operations Manager 的整合](log-analytics-om-agents.md)時傳遞之組態頻率的詳細資訊。

如果代理程式無法連接到 Log Analytics 或 Operations Manager，它將會繼續收集資料，以便在建立連線時進行傳遞。  如果資料量達到用戶端的快取大小上限，或者代理程式無法在 24 小時內建立連線，可能就會遺失資料。

## <a name="log-analytics-records"></a>Log Analytics 記錄
Log Analytics 收集的所有資料都會以記錄形式儲存在 OMS 儲存機制中。  不同資料來源所收集的記錄會有自己的一組屬性，並由其 **類型** 屬性來識別。  如需每種記錄類型的詳細資訊，請參閱各資料來源和方案的文件。

## <a name="next-steps"></a>後續步驟
* 了解可將功能加入 Log Analytics 並會將資料收集到 OMS 儲存機制的 [方案](log-analytics-add-solutions.md) 。
* 了解 [記錄搜尋](log-analytics-log-searches.md) ，其可分析從資料來源和方案所收集的資料。  
* 設定[警示](log-analytics-alerts.md)，以便從資料來源和方案收集到重要資料時主動通知您。

