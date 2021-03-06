---
title: "在 IntelliJ 中建立基本的 Azure Web 應用程式"
description: "本教學課程將示範如何使用適用於 IntelliJ 的 Azure 工具組來建立 Azure 的 Hello World Web 應用程式。"
services: app-service\web
documentationcenter: java
author: selvasingh
manager: routlaw
editor: 
ms.assetid: 75ce7b36-e3ae-491d-8305-4b42ce37db4e
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: Java
ms.topic: article
ms.date: 08/20/2017
ms.author: robmcm;asirveda
ms.translationtype: HT
ms.sourcegitcommit: a16daa1f320516a771f32cf30fca6f823076aa96
ms.openlocfilehash: 260302a49c65106728e0aa8347e9fb89a8c8c270
ms.contentlocale: zh-tw
ms.lasthandoff: 09/02/2017

---
# <a name="create-a-basic-azure-web-app-in-intellij"></a>在 IntelliJ 中建立基本的 Azure Web 應用程式

本教學課程示範如何使用 [Azure Toolkit for IntelliJ (適用於 IntelliJ 的 Azure 工具組)]，建立基本的 Hello World 應用程式，並做為 Web 應用程式部署到 Azure。

> [!NOTE]
> 
> 適用於 IntelliJ 的 Azure 工具組在 2017 年 8 月更新，有不同的工作流程。 考量到這點，本文包含兩個不同的部分：
>
> * 第一部分說明如何使用適用於 IntelliJ 的 Azure 工具組 2017 年 8 月 (含) 以後版本的來建立 Hello World Web 應用程式。
>
> * 本文第二個部分將示範如何使用工具組的 2017 年 4 月 (含) 以前版本建立 Hello World web 應用程式。
> 

[!INCLUDE [azure-toolkit-for-intellij-prerequisites](../../includes/azure-toolkit-for-intellij-prerequisites.md)]

## <a name="create-a-hello-world-web-app-by-using-the-version-307-or-later-toolkit"></a>使用 3.0.7 版或以後版本的工具組來建立 Hello World Web 應用程式

### <a name="create-a-new-web-app-project"></a>建立新的 Web 應用程式專案

1. 使用 [適用於 IntelliJ 的 Azure 工具組登入指示] 文章中的步驟來啟動 IntelliJ 和登入您的 Azure 帳戶。

1. 按一下 [檔案] 功能表，按一下 [新增]，然後按一下 [專案]。
   
   ![建立新專案][file-new-project]

1. 在 **新增專案** 對話方塊中，選取 **Maven** ，然後選取 **maven-archetype-webapp** ，再按一下 [下一步]。
   
   ![選擇 Maven archetype webapp][maven-archetype-webapp]
   
1. 指定 Web 應用程式的 [GroupId] 和 [ArtifactId]，然後按一下 [下一步]。
   
   ![指定 GroupId 和 ArtifactId][groupid-and-artifactid]

1. 自訂任何 Maven 設定或接受預設值，然後按一下 [下一步]。
   
   ![指定 Maven 設定][maven-options]

1. 指定專案名稱和位置，然後按一下 [完成]。
   
   ![指定專案名稱][project-name]

1. 在 IntelliJ 的 [專案總管] 檢視中，依序展開 [src]、[main] 和 [webapp]，然後按兩下 [index.jsp]。
   
   ![開啟索引頁面][open-index-page]

1. 當 index.jsp 檔案在 IntelliJ 中開啟時，加入文字以動態顯示 **Hello World!** (在現有 `<body>` 元素內)。 您已更新的 `<body>` 內容看起來應該與下列範例類似：
   
   ```java
   <body><b><% out.println("Hello World!"); %></b></body>
   ``` 

   ![編輯索引頁面][edit-index-page]

1. 儲存 index.jsp。

### <a name="deploy-your-web-app-to-azure"></a>將 Web 應用程式部署至 Azure

1. 在 IntelliJ 的 [專案總管] 畫面，以滑鼠右鍵按一下您的專案，並選擇 [Azure]，然後選擇 [在 Web 應用程式上執行]。
   
   ![[在 Web 應用程式上執行] 功能表][run-on-web-app-menu]

1. 在 [在 Web 應用程式上執行] 對話方塊中，可以選擇下列其中一個選項：

   * 請選擇現有 Web 應用程式 (如果有)，然後按一下 [執行]。

      ![[在 Web 應用程式上執行] 對話方塊][run-on-web-app-dialog]

   * 按一下 [建立新的 Web 應用程式]。 如果您選擇建立新的 Web 應用程式，請指定 Web 應用程式的必要資訊，然後按一下 [執行]。

      ![建立新的 Web 應用程式][create-new-web-app-dialog]

1. 工具組成功部署 Web 應用程式時，會顯示狀態訊息，也會顯示已部署的 Web 應用程式本身的 URL。

   ![部署成功][successfully-deployed]

1. 您可以使用狀態訊息中提供的連結，瀏覽至您的 Web 應用程式。

   ![瀏覽 Web 應用程式][browse-web-app]

1. 發佈 Web 應用程式之後，系統會將您的設定儲存為預設值，您可以按一下工具列上的綠色箭號圖示，在 Azure 上執行您的應用程式。 您可以透過按一下 Web 應用程式的下拉式功能表，然後按一下 [編輯組態]，修改您的設定。

   ![[編輯組態] 功能表][edit-configuration-menu]

1. 顯示 [執行/偵錯組態] 對話方塊時，您可以修改任何預設設定，然後按一下 [確定]。

   ![[編輯組態] 對話方塊][edit-configuration-dialog]

<hr />

## <a name="create-a-hello-world-web-app-by-using-the-version-306-or-earlier-toolkit"></a>使用 3.0.6 版 (或) 以前版本的工具組建立 Hello World Web 應用程式

### <a name="create-a-new-web-app-project"></a>建立新的 Web 應用程式專案

1. 啟動 IntelliJ，按一下 [檔案] 功能表，然後依序按一下 [新增] 及 [專案]。
   
   ![專案 > 新增專案][02]

2. 在 [新增專案] 對話方塊中，依序選取 [Java]、[Web 應用程式] 及 [新增]，以新增專案 SDK。
   
   ![New Project Dialog][03a]
   
3. 在 [選取 JDK 的主目錄] 對話方塊中，選取 JDK 安裝所在的資料夾，然後按一下 [確定]。 在 [新增專案] 對話方塊中，按 [下一步] 繼續。
   
   ![指定 JDK 主目錄][03b]

4. 基於本教學課程的目的，將專案命名為 **Java-Web-App-On-Azure**，然後按一下 [完成]。
   
   ![New Project Dialog][04]

5. 在 IntelliJ 的 [專案總管] 檢視中，依序展開 [Java-Web-App-On-Azure] 和 [web]，然後按兩下 [index.jsp]。
   
   ![開啟索引頁面][05c]

6. 當 index.jsp 檔案在 IntelliJ 中開啟時，加入文字以動態顯示 **Hello World!** (在現有 `<body>` 元素內)。 您已更新的 `<body>` 內容看起來應該與下列範例類似：
   
   ```java
   <body><b><% out.println("Hello World!"); %></b></body>
   ```

7. 儲存 index.jsp。

### <a name="deploy-your-web-app-to-azure"></a>將 Web 應用程式部署至 Azure
您有數種方式可以將 Java Web 應用程式部署至 Azure。 本教學課程說明其中一個最簡單的方式：將您的應用程式部署至 Azure Web 應用程式容器，無需特殊的專案類型或額外的工具。 Azure 會為您提供 JDK 及 Web 容器軟體，因此您不需要自己上傳；只需要您的 Java Web 應用程式。 如此一來，您的應用程式發行程序只需數秒，連一分鐘都不用。

發佈您的應用程式之前，必須先設定模組設定。 若要這樣做，請使用下列步驟：

1. 在 IntelliJ 的專案總管中，以滑鼠右鍵按一下 [Java-Web-App-On-Azure]  專案。 當操作功能表出現時，按一下 [開啟模組設定]。

   ![開啟模組設定][05a]

2. 當 [專案結構] 對話方塊出現時：

   a. 按一下 [專案設定] 清單中的 [構件]。

   b. 變更 [名稱] 方塊中的構件名稱，使其不包含空格或特殊字元；這是必要動作，因為此名稱將用於統一資源識別項 (URI) 中。

   c. 將 [類型] 變更為 [Web 應用程式：封存]。

   d. 按一下 [確定] 以關閉 [專案結構] 對話方塊。

   ![開啟模組設定][05b]

完成設定您的模組設定時，您可以使用下列步驟來將應用程式發佈到 Azure：

1. 在 IntelliJ 的專案總管中，以滑鼠右鍵按一下 [Java-Web-App-On-Azure]  專案。 操作功能表顯示時，選取 [Azure]，然後按一下 [發佈為 Azure Web 應用程式]
   
   ![Azure 發佈操作功能表][06]

2. 如果尚未從 IntelliJ 登入 Azure，系統會提示您登入 Azure 帳戶。 (如果您有多個 Azure 帳戶，登入程序期間的某些提示即使內容相同也可能會出現多次。 發生此情況時，請遵循登入指示繼續。)
   
   ![Azure 登入對話方塊][07]

3. 在您成功登入 Azure 帳戶後，[管理訂用帳戶] 對話方塊將會顯示與您的認證相關聯的訂用帳戶清單。 (如果列出多個訂用帳戶，而您只想使用其中幾個帳戶，您可以選擇取消選取不想要使用的訂用帳戶。)當您選取訂用帳戶之後，按一下 [關閉] 。
   
   ![管理訂用帳戶][08]

4. 當 [部署至 Azure Web 應用程式容器]  對話方塊出現時，它會顯示您先前建立的所有 Web 應用程式容器；如果您尚未建立任何容器，清單將會是空白的。
   
   ![應用程式容器][09]

5. 如果您之前尚未建立 Azure Web 應用程式容器，或您想要將應用程式發佈到新的容器中，請使用下列步驟。 否則，請選取現有的 Web 應用程式容器，並跳至以下的步驟 6。
   
   a. 按一下 **+** 記號。
      
      ![新增應用程式容器][10]

   b. [新增 Web 應用程式容器]  對話方塊會隨即顯示，此對話方塊將用來進行接下來的幾個步驟。
      
      ![新增應用程式容器][11a]
   
   c. 為您的 Web 應用程式容器輸入 **DNS 標籤** ，這會為您在 Azure 中的 Web 應用程式構成主機 URL 的分葉 DNS 標籤。 請注意，名稱必須可用，且符合 Azure Web 應用程式命名需求。

   d. 在 [Web 容器]  下拉式功能表中，為您的應用程式選取適當的軟體。
      
      目前，您可以從 Tomcat 8、Tomcat 7 或 Jetty 9 選擇。 所選軟體最新發行的版本由 Azure 提供，會在最新發行的 JDK 8 (由 Oracle 建立並由 Azure 提供) 中運作。

   e. 在 [訂用帳戶]  下拉式選單中，選取您希望此部署使用的訂用帳戶。

   f. 在 [資源群組]  下拉式功能表中，選取您要與 Web 應用程式相關聯的資源群組。 (Azure 資源群組可讓您將相關的資源分在同一組，方便一次刪除。)
      
      您可以選取現有的資源群組 (如果有)，並略過下方步驟 g，或使用以下步驟建立新的資源群組：
      
      * 在 [資源群組] 下拉式功能表中，選取 [&lt;&lt; 建立新的資源群組 &gt;&gt;]。
      * [新增資源群組]  對話方塊會隨即顯示：
        
         ![新增資源群組][12]

      * 在 [名稱] 文字方塊中，為新的資源群組指定名稱。
      * 在 [區域] 下拉式功能表中，為資源群組選取適當的 Azure 資料中心位置。
      * 按一下 [確定] 。

   g. [App Service 方案]  下拉式功能表會列出與您選取之資源群組相關聯的應用程式服務方案。 (App Service 方案會指定特定資訊，例如您 Web 應用程式的位置、定價層以及計算執行個體大小。 單一 App Service 方案可用於多個 Web Apps，這也就是要與特定 Web 應用程式部署分開維護的原因。)
      
      您可以選取現有的 App Service 方案 (如果有)，並略過下方步驟 h，或使用以下步驟建立新的 App Service 方案：
      
      * 在 [App Service 方案] 下拉式功能表中，選取 [&lt;&lt; 建立新的 App Service 方案 &gt;&gt;]。
      * [新增 App Service 方案]  對話方塊會隨即顯示：
        
         ![新增 App Service 方案][13]

      * 在 [名稱] 文字方塊中，為新的 App Service 方案指定名稱。
      * 在 [位置] 下拉式功能表中，為該方案選取適當的 Azure 資料中心位置。
      * 在 [定價層] 下拉式功能表中，為方案選取適當的價格。 針對測試用途，您可以選擇 [免費] 。
      * 在 [執行個體大小] 下拉式功能表中，為方案選取適當的執行個體大小。 針對測試用途，您可以選擇 [小型] 。
      * 按一下 [確定] 。

   h. (選擇性) 根據預設，Azure 會自動將最新的 Java 8 散發套件部署到 Web 應用程式容器，成為您的 JVM。 不過，您可以選取不同的 JVM 版本和散發套件。 若要這樣做，請使用下列步驟：
      
      * 在 [新增 Web 應用程式容器] 對話方塊中，按一下 [JDK] 索引標籤。
      * 您可以選擇下列其中一個選項：
        
         * 部署 Azure 所提供的預設 JDK
         * 從 Azure 提供的其他 JDK 下接式清單中部署協力廠商 JDK
         * 部署自訂 JDK，這必須封裝為 ZIP 檔案，而且公開可用或位於您的 Azure 儲存體帳戶中
        
      ![新增應用程式容器 JDK 索引標籤][11b]

   i. 一旦您完成所有上述步驟之後，[New Web App Container] \(新增 Web 應用程式容器) 對話方塊看起來應該如下圖所示：
      
      ![新增應用程式容器][14]
   
   j. 按一下 [確定]  來完成建立新的 Web 應用程式容器。
       
      等待數秒鐘，讓 Web 應用程式容器清單重新整理；接著，您應該會在清單中看到新建立的 Web 應用程式容器已被選取。

6. 現在您已準備好將 Web 應用程式初始部署至 Azure；按一下 [確定]  ，將您的 Java 應用程式部署至選取的 Web 應用程式容器。 根據預設，您的應用程式將會部署為應用程式伺服器的子目錄。 如果您想要部署為根應用程式，請選取 [部署到根目錄] 核取方塊，然後按一下 [確定]。
   
   ![部署至 Azure][15]

7. 接下來，您應該會看到 [Azure 活動記錄檔]  檢視，它會指出 Web 應用程式的部署狀態。
   
   ![進度指示器][16]
   
   將您的 Web 應用程式部署至 Azure 的程序，應該只需幾秒鐘即可完成。 當您的應用程式就緒時，您會看見在 [狀態]  欄中出現名稱為**已發佈**的連結。 當您按一下連結時，它會帶您到已部署的 Web 應用程式首頁，或者您也可以使用下一節中的步驟，以瀏覽至您的 Web 應用程式。

### <a name="browsing-to-your-web-app-on-azure"></a>瀏覽至您在 Azure 上的 Web 應用程式
若要瀏覽至您在 Azure 上的 Web 應用程式，您可以使用 [Azure 總管]  檢視。

如果 [Azure 總管] 檢視尚未開啟，您可以依序按一下 IntelliJ 中的 [檢視] 功能表、[工具視窗]和 [服務總管] 來開啟。 如果您之前尚未登入，系統將會提示您登入。

顯示 [Azure 總管] 檢視之後，按照下列這些步驟來瀏覽至您的 Web 應用程式： 

1. 展開 [Azure]  節點。
2. 展開 [Web Apps]  節點。 
3. 以滑鼠右鍵按一下所需的 Web 應用程式。
4. 操作功能表出現時，按一下 [在瀏覽器中開啟] 。
   
   ![瀏覽 Web 應用程式][17]

### <a name="updating-your-web-app"></a>更新 Web 應用程式
更新現有執行中的 Azure Web 應用程式是一項快速又簡單的程序，而且您有兩個更新選項：

* 您可以更新現有 Java Web 應用程式的部署。
* 您可以將其他的 Java 應用程式發佈到相同的 Web 應用程式容器。

在任一種情況中，程序都是相同的，而且只需幾秒鐘：

1. 在 IntelliJ 專案總管中，以滑鼠右鍵按一下您要更新或新增到現有 Web 應用程式容器的 Java 應用程式。
2. 操作功能表顯示時，選取 [Azure]，然後選取 [發佈為 Azure Web 應用程式...]
3. 由於您之前已經登入，因此會看到您現有 Web 應用程式容器的清單。 選取您要發佈或重新發佈 Java 應用程式的 Web 應用程式容器，然後按一下 [確定] 。

幾秒鐘之後，[Azure 活動記錄檔] 檢視將會將您已更新的部署顯示為 [已發佈]，而您將可以在網頁瀏覽器中確認已更新的應用程式。

### <a name="starting-stopping-or-restarting-an-existing-web-app"></a>啟動、停止或重新啟動現有的 Web 應用程式
若要啟動或停止現有的 Azure Web 應用程式容器 (包括其中所有已部署的 Java 應用程式)，您可以使用 [Azure 總管]  檢視。

如果 [Azure 總管] 檢視尚未開啟，您可以依序按一下 IntelliJ 中的 [檢視] 功能表、[工具視窗]和 [服務總管] 來開啟。 如果您之前尚未登入，系統將會提示您登入。

顯示 [Azure 總管] 之後，按照下列這些步驟來啟動或停止您的 Web 應用程式： 

1. 展開 [Azure]  節點。
2. 展開 [Web Apps]  節點。 
3. 以滑鼠右鍵按一下所需的 Web 應用程式。
4. 當操作功能表出現時，按一下 [啟動]、[停止] 或 [重新啟動]。 請注意，功能表選項是內容感知的，因此您只能停止執行中的 Web 應用程式，或是啟動目前尚未執行的 Web 應用程式。
   
   ![停止 Web 應用程式][18]

## <a name="next-steps"></a>後續步驟

[!INCLUDE [azure-toolkit-additional-resources](../../includes/azure-toolkit-additional-resources.md)]

如需建立 Azure Web Apps 的詳細資訊，請參閱 [Web 應用程式概觀]。

[!INCLUDE [app-service-web-try-app-service](../../includes/app-service-web-try-app-service.md)]

<!-- URL List -->

[Azure Toolkit for Eclipse]: ../azure-toolkit-for-eclipse.md
[Azure Toolkit for IntelliJ (適用於 IntelliJ 的 Azure 工具組)]: ../azure-toolkit-for-intellij.md
[Create a Hello World Web App for Azure in Eclipse]: ./app-service-web-eclipse-create-hello-world-web-app.md
[Create a Hello World Web App for Azure in IntelliJ]: ./app-service-web-intellij-create-hello-world-web-app.md
[Installing the Azure Toolkit for Eclipse]: ../azure-toolkit-for-eclipse-installation.md
[Installing the Azure Toolkit for IntelliJ]: ../azure-toolkit-for-intellij-installation.md
[What's New in the Azure Toolkit for Eclipse]: ../azure-toolkit-for-eclipse-whats-new.md
[What's New in the Azure Toolkit for IntelliJ]: ../azure-toolkit-for-intellij-whats-new.md

[Azure Java Developer Center]: https://azure.microsoft.com/develop/java/
[Web 應用程式概觀]: ./app-service-web-overview.md
[Apache Tomcat]: http://tomcat.apache.org/
[Jetty]: http://www.eclipse.org/jetty/

<!-- IMG List -->

[01]: ./media/app-service-web-intellij-create-hello-world-web-app/01-Web-Page.png
[02]: ./media/app-service-web-intellij-create-hello-world-web-app/02-File-New-Project.png
[03a]: ./media/app-service-web-intellij-create-hello-world-web-app/03-New-Project-Dialog.png
[03b]: ./media/app-service-web-intellij-create-hello-world-web-app/03-New-Project-SDK-Dialog.png
[04]: ./media/app-service-web-intellij-create-hello-world-web-app/04-New-Project-Dialog.png
[05a]: ./media/app-service-web-intellij-create-hello-world-web-app/05-Open-Module-Settings.png
[05b]: ./media/app-service-web-intellij-create-hello-world-web-app/05-Project-Structure-Dialog.png
[05c]: ./media/app-service-web-intellij-create-hello-world-web-app/05-Open-Index-Page.png
[06]: ./media/app-service-web-intellij-create-hello-world-web-app/06-Azure-Publish-Context-Menu.png
[07]: ./media/app-service-web-intellij-create-hello-world-web-app/07-Azure-Log-In-Dialog.png
[08]: ./media/app-service-web-intellij-create-hello-world-web-app/08-Manage-Subscriptions.png
[09]: ./media/app-service-web-intellij-create-hello-world-web-app/09-App-Containers.png
[10]: ./media/app-service-web-intellij-create-hello-world-web-app/10-Add-App-Container.png
[11a]: ./media/app-service-web-intellij-create-hello-world-web-app/11-New-App-Container.png
[11b]: ./media/app-service-web-intellij-create-hello-world-web-app/11-New-App-Container-JDK-Tab.png
[12]: ./media/app-service-web-intellij-create-hello-world-web-app/12-New-Resource-Group.png
[13]: ./media/app-service-web-intellij-create-hello-world-web-app/13-New-App-Service-Plan.png
[14]: ./media/app-service-web-intellij-create-hello-world-web-app/14-New-App-Container.png
[15]: ./media/app-service-web-intellij-create-hello-world-web-app/15-Deploy-To-Azure.png
[16]: ./media/app-service-web-intellij-create-hello-world-web-app/16-Progress-Indicator.png
[17]: ./media/app-service-web-intellij-create-hello-world-web-app/17-Browse-Web-App.png
[18]: ./media/app-service-web-intellij-create-hello-world-web-app/18-Stop-Web-App.png

[file-new-project]: ./media/app-service-web-intellij-create-hello-world-web-app/file-new-project.png
[maven-archetype-webapp]: ./media/app-service-web-intellij-create-hello-world-web-app/maven-archetype-webapp.png
[groupid-and-artifactid]: ./media/app-service-web-intellij-create-hello-world-web-app/groupid-and-artifactid.png
[maven-options]: ./media/app-service-web-intellij-create-hello-world-web-app/maven-options.png
[project-name]: ./media/app-service-web-intellij-create-hello-world-web-app/project-name.png
[open-index-page]: ./media/app-service-web-intellij-create-hello-world-web-app/open-index-page.png
[edit-index-page]: ./media/app-service-web-intellij-create-hello-world-web-app/edit-index-page.png
[run-on-web-app-menu]: ./media/app-service-web-intellij-create-hello-world-web-app/run-on-web-app-menu.png
[run-on-web-app-dialog]: ./media/app-service-web-intellij-create-hello-world-web-app/run-on-web-app-dialog.png
[create-new-web-app-dialog]: ./media/app-service-web-intellij-create-hello-world-web-app/create-new-web-app-dialog.png
[successfully-deployed]: ./media/app-service-web-intellij-create-hello-world-web-app/successfully-deployed.png
[browse-web-app]: ./media/app-service-web-intellij-create-hello-world-web-app/browse-web-app.png
[edit-configuration-menu]: ./media/app-service-web-intellij-create-hello-world-web-app/edit-configuration-menu.png
[edit-configuration-dialog]: ./media/app-service-web-intellij-create-hello-world-web-app/edit-configuration-dialog.png

