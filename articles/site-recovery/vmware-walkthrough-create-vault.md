---
title: "使用 Azure Site Recovery 針對 VMware 到 Azure 的複寫設定保存庫 | Microsoft Docs"
description: "摘要說明使用 Azure Site Recovery 針對 VMware 到 Azure 的複寫設定保存庫時所需的步驟"
services: site-recovery
documentationcenter: 
author: rayne-wiselman
manager: carmonm
editor: 
ms.assetid: 8bce940e-f19f-4418-8360-aee7b073519a
ms.service: site-recovery
ms.workload: storage-backup-recovery
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/27/2017
ms.author: raynew
ms.translationtype: Human Translation
ms.sourcegitcommit: 138f04f8e9f0a9a4f71e43e73593b03386e7e5a9
ms.openlocfilehash: dca95ad46b8de587140c3573ba6ed5702a122032
ms.contentlocale: zh-tw
ms.lasthandoff: 06/29/2017


---
# <a name="step-7-set-up-a-vault-for-vmware-replication-to-azure"></a>步驟 7：針對 VMware 到 Azure 的複寫設定保存庫


本文說明如何在 Azure 入口網站中使用 [Azure Site Recovery](site-recovery-overview.md) 服務來設定保存庫，並指定要將哪些項目從內部部署位置複寫至 Azure。


請在本文下方或 [Azure 復原服務論壇](https://social.msdn.microsoft.com/forums/azure/home?forum=hypervrecovmgr)上張貼意見或問題。




## <a name="create-a-recovery-services-vault"></a>建立復原服務保存庫

[!INCLUDE [site-recovery-create-vault](../../includes/site-recovery-create-vault.md)]

## <a name="select-a-protection-goal"></a>選取保護目標

選取您要複寫的項目以及您要複寫到的位置。

1. 按一下 [復原服務保存庫] > 保存庫。
2. 在 [資源] 功能表中，按一下 [Site Recovery] > [準備基礎結構] > [保護目標]。
3. 在 [保護目標] 中選取 [至 Azure] > [是，使用 VMware vSphere Hypervisor]。



## <a name="next-steps"></a>後續步驟

移至[步驟 8：設定來源和目標](vmware-walkthrough-source-target.md)

