---
title: "Microsoft Azure 雲端服務之部署問題的常見問題集 | Microsoft Docs"
description: "本文列出 Microsoft Azure 雲端服務之部署的相關常見問題集。"
services: cloud-services
documentationcenter: 
author: genlin
manager: cshepard
editor: 
tags: top-support-issue
ms.assetid: 84985660-2cfd-483a-8378-50eef6a0151d
ms.service: cloud-services
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 7/10/2017
ms.author: genli
ms.translationtype: Human Translation
ms.sourcegitcommit: db18dd24a1d10a836d07c3ab1925a8e59371051f
ms.openlocfilehash: 9b788b1d95c821a4bb76cd4dea1d689d36e2f92b
ms.contentlocale: zh-tw
ms.lasthandoff: 06/15/2017


---
# <a name="deployment-issues-for-azure-cloud-services-frequently-asked-questions-faqs"></a>Azure 雲端服務之部署問題：常見問題集 (FAQ)

本文包含 [Microsoft Azure 雲端服務](https://azure.microsoft.com/services/cloud-services)之部署問題的相關常見問題集。 您也可以參閱 [雲端服務 VM 大小頁面](cloud-services-sizes-specs.md) 以取得大小資訊。

[!INCLUDE [support-disclaimer](../../includes/support-disclaimer.md)]

## <a name="why-does-deploying-a-cloud-service-to-the-staging-slot-sometimes-fail-with-a-resource-allocation-error-if-there-is-already-an-existing-deployment-in-the-production-slot"></a>如果生產位置中已經有現有的部署，為什麼將雲端服務部署至暫存位置時有時候會失敗，並出現資源配置錯誤？
如果某個雲端服務在任一位置具有部署，整個雲端服務就會釘選到特定的叢集。 這表示如果某個部署已存在生產位置，新的預備部署就只能配置在與生產位置相同的叢集中。

當您雲端服務所在的叢集中沒有足夠的實體計算資源可滿足您的部署要求時，就會發生配置失敗。

如需緩和這種配置失敗的協助，請參閱[雲端服務配置失敗：解決方案](cloud-services-allocation-failures.md#solutions)。

## <a name="why-does-scaling-up-or-scaling-out-a-cloud-service-deployment-sometimes-result-in-allocation-failure"></a>為什麼將雲端服務部署向上擴充或相應放大有時會造成配置失敗？
部署雲端服務時，通常會釘選到特定的叢集。 這表示向上擴充/相應放大現有的雲端服務必須將新的執行個體配置在相同叢集中。 如果叢集已接近其容量，或無法使用所需的 VM 大小/類型，要求可能就會失敗。

如需緩和這種配置失敗的協助，請參閱[雲端服務配置失敗：解決方案](cloud-services-allocation-failures.md#solutions)。

## <a name="why-does-deploying-a-cloud-service-into-an-affinity-group-sometimes-result-in-allocation-failure"></a>為什麼將雲端服務部署至同質群組時，有時會造成配置失敗？
部署到空白雲端服務的新部署可經由該區域中任一叢集的網狀架構配置，除非雲端服務已釘選到某個同質群組。 將在相同的叢集中嘗試部署到相同的同質群組。 如果叢集逼近容量上限，則要求可能會失敗。

如需緩和這種配置失敗的協助，請參閱[雲端服務配置失敗：解決方案](cloud-services-allocation-failures.md#solutions)。

## <a name="why-does-changing-vm-size-or-adding-a-new-vm-to-an-existing-cloud-service-sometimes-result-in-allocation-failure"></a>為什麼變更 VM 大小或將新的 VM 新增至現有雲端服務時，有時會造成配置失敗？
資料中心內的叢集可能會有電腦類型的不同設定 (例如，A 系列、Av2 系列、D 系列、Dv2 系列、G 系列、H 系列等)。 但並非所有的叢集都一定會有所有種類的 VM。 例如，如果您嘗試新增到雲端服務的 D 系列 VM 已部署在僅限 A 系列的叢集中，就會發生配置失敗。 如果您嘗試變更 VM SKU 大小 (例如，從 A 系列切換至 D 系列)，也會發生這個問題。

如需緩和這種配置失敗的協助，請參閱[雲端服務配置失敗：解決方案](cloud-services-allocation-failures.md#solutions)。

若要檢查您地區中可用的大小，請參閱 [Microsoft Azure：依區域提供的產品](https://azure.microsoft.com/regions/services)。

## <a name="why-does-deploying-a-cloud-service-sometime-fail-due-to-limitsquotasconstraints-on-my-subscription-or-service"></a>為什麼部署雲端服務有時會因為我訂用帳戶或服務的限制/配額/條件約束而失敗？
如果配置所需的資源超過預設值，或超過您區域/資料中心層級所允許的最大配額，雲端服務部署就可能會失敗。 如需詳細資訊，請參閱[雲端服務限制](../azure-subscription-service-limits.md#cloud-services-limits)。

您也可以在入口網站追蹤訂用帳戶目前的使用量/配額：Azure 入口網站  => 訂用帳戶  => \<適當的訂用帳戶 > => 使用方式 + 配額。

也可以透過 Azure 計費 API 擷取資源使用量/耗用量的相關資訊。 請參閱 [Azure 資源使用情況 API (預覽)](../billing/billing-usage-rate-card-overview.md#azure-resource-usage-api-preview)。

## <a name="how-can-i-change-the-size-of-a-deployed-cloud-service-vm-without-redeploying-it"></a>如何在不重新部署的情況下變更已部署之雲端服務 VM 的大小？
您無法在不重新部署的情況下變更已部署之雲端服務的 VM 大小。 VM 大小已內建於 CSDEF，只可使用重新部署來進行更新。

如需詳細資訊，請參閱[如何更新雲端服務](cloud-services-update-azure-service.md)。

 

