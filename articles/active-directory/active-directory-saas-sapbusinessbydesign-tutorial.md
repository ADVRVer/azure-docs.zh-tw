---
title: "教學課程：Azure Active Directory 與 SAP Business ByDesign 整合 | Microsoft Docs"
description: "了解如何設定 Azure Active Directory 與 SAP Business ByDesign 之間的單一登入。"
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 82938920-33ba-47cb-b141-511b46d19e66
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/25/2017
ms.author: jeedes
ms.translationtype: HT
ms.sourcegitcommit: 74b75232b4b1c14dbb81151cdab5856a1e4da28c
ms.openlocfilehash: ab76a0ac1ef954efd3c66e6f565514b889ed9444
ms.contentlocale: zh-tw
ms.lasthandoff: 07/26/2017

---
# <a name="tutorial-azure-active-directory-integration-with-sap-business-bydesign"></a>教學課程：Azure Active Directory 與 SAP Business ByDesign 整合

在本教學課程中，您會了解如何整合 SAP Business ByDesign 與 Azure Active Directory (Azure AD)。

SAP Business ByDesign 與 Azure AD 整合提供下列優點：

- 您可以在 Azure AD 中控制可存取 SAP Business ByDesign 的人員。
- 您可以讓使用者使用他們的 Azure AD 帳戶自動登入 SAP Business ByDesign (單一登入)。
- 您可以在 Azure 入口網站中集中管理您的帳戶。

如果您想要了解有關 SaaS 應用程式與 Azure AD 之整合的更多詳細資料，請參閱[什麼是搭配 Azure Active Directory 的應用程式存取和單一登入](active-directory-appssoaccess-whatis.md)。

## <a name="prerequisites"></a>必要條件

若要設定 Azure AD 與 SAP Business ByDesign 整合，您需要下列項目：

- Azure AD 訂用帳戶
- 已啟用 SAP Business ByDesign 單一登入功能的訂用帳戶

> [!NOTE]
> 若要測試本教學課程中的步驟，我們不建議使用生產環境。

若要測試本教學課程中的步驟，您應該遵循這些建議：

- 除非必要，否則請勿使用生產環境。
- 如果您沒有 Azure AD 試用環境，您可以[取得一個月試用](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>案例描述
在本教學課程中，您會在測試環境中測試 Azure AD 單一登入。 本教學課程中說明的案例由二個主要建置組塊組成：

1. 從資源庫新增 SAP Business ByDesign
2. 設定並測試 Azure AD 單一登入

## <a name="adding-sap-business-bydesign-from-the-gallery"></a>從資源庫新增 SAP Business ByDesign
若要設定 SAP Business ByDesign 與 Azure AD 整合，您需要從資源庫將 SAP Business ByDesign 加入到受管理的 SaaS 應用程式清單中。

**若要從資源庫加入 SAP Business ByDesign，請執行下列步驟：**

1. 在 **[Azure 入口網站](https://portal.azure.com)**的左方瀏覽窗格中，按一下 [Azure Active Directory] 圖示。 

    ![Azure Active Directory 按鈕][1]

2. 瀏覽至 [企業應用程式]。 然後移至 [所有應用程式]。

    ![企業應用程式刀鋒視窗][2]
    
3. 若要新增新的應用程式，請按一下對話方塊頂端的 [新增應用程式] 按鈕。

    ![新增應用程式按鈕][3]

4. 在搜尋方塊中，輸入 **SAP Business ByDesign**，從結果面板中選取 [SAP Business ByDesign]，然後按一下 [新增] 按鈕以新增應用程式。

    ![結果清單中的 SAP Business ByDesign](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>設定和測試 Azure AD 單一登入

在本節中，您會以名為 "Britta Simon" 的測試使用者身分，使用 SAP Business ByDesign 設定及測試 Azure AD 單一登入。

若要讓單一登入運作，Azure AD 必須知道 SAP Business ByDesign 與 Azure AD 中互相對應的使用者。 換句話說，必須在 Azure AD 使用者與 SAP Business ByDesign 中的相關使用者之間建立連結關聯性。

在 SAP Business ByDesign 中，將 Azure AD 中**使用者名稱**的值指派為 **Username** 的值，以建立連結關聯性。

若要設定及測試對 SAP Business ByDesign 的 Azure AD 單一登入，您需要完成下列建置組塊：

1. **[設定 Azure AD 單一登入](#configure-azure-ad-single-sign-on)** - 讓您的使用者能夠使用此功能。
2. **[建立 Azure AD 測試使用者](#create-an-azure-ad-test-user)** - 使用 Britta Simon 測試 Azure AD 單一登入。
3. **[建立 SAP Business ByDesign 測試使用者](#create-an-sap-business-bydesign-test-user)** - 使 SAP Business ByDesign 中對應的 Britta Simon 連結到該使用者在 Azure AD 中的代表項目。
4. **[指派 Azure AD 測試使用者](#assign-the-azure-ad-test-user)** - 讓 Britta Simon 能夠使用 Azure AD 單一登入。
5. **[測試單一登入](#test-single-sign-on)**，驗證組態是否能運作。

### <a name="configure-azure-ad-single-sign-on"></a>設定 Azure AD 單一登入

在本節中，您會於 Azure 入口網站啟用 Azure AD 單一登入，並在您的 SAP Business ByDesign 應用程式中設定單一登入。

**若要使用 SAP Business ByDesign 設定 Azure AD 單一登入，請執行下列步驟：**

1. 在 Azure 入口網站的 [SAP Business ByDesign] 應用程式整合頁面上，按一下 [單一登入]。

    ![設定單一登入連結][4]

2. 在 [單一登入] 對話方塊上，於 [模式] 選取 [SAML 登入]，以啟用單一登入。
 
    ![單一登入對話方塊](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_samlbase.png)

3. 在 [SAP Business ByDesign 網域及 URL] 區段中，執行下列步驟：

    ![SAP Business ByDesign 網域及 URL 單一登入資訊](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_url.png)

    a. 在 [登入 URL] 文字方塊中，使用下列模式輸入 URL︰`https://<servername>.sapbydesign.com`

    b. 在 [識別碼] 文字方塊中，使用下列模式輸入 URL：`https://<servername>.sapbydesign.com`

    > [!NOTE] 
    > 這些都不是真正的值。 使用實際的「登入 URL」及「識別碼」來更新這些值。 請連絡 [SAP Business ByDesign 用戶端支援小組](https://www.sap.com/products/cloud-analytics.support.html)以取得這些值。

4. 在 [使用者屬性] 區段中，執行下列步驟：

    ![[SAP Business ByDesign 屬性] 區段](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_attribute.png)
    
    a. 在 [使用者識別碼] 清單中，選取 **ExtractMailPrefix()** 函式。
    
    b.這是另一個 C# 主控台應用程式。 從 [郵件] 清單中，選取您想要用於實作的使用者屬性。 例如，如果您想要使用 EmployeeID 為唯一的使用者識別碼，而且已在 ExtensionAttribute2 中儲存屬性值，則選取 [user.extensionattribute2]。     

5. 在 [SAML 簽署憑證] 區段上，按一下 [中繼資料 XML]，然後將中繼資料檔案儲存在您的電腦上。

    ![憑證下載連結](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_certificate.png) 

6. 按一下 [儲存]  按鈕。

    ![設定單一登入儲存按鈕](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_400.png)

7. 在 [SAP Business ByDesign 設定] 區段中，按一下 [設定 SAP Business ByDesign] 可開啟 [設定登入] 視窗。 從 [快速參考] 區段中複製 [SAML 單一登入服務 URL]。

    ![SAP Business ByDesign 設定](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_configure.png) 

8. 為了設定應用程式的 SSO，請執行下列步驟：
   
    a. 使用系統管理員權限登入 SAP Business ByDesign 入口網站。
   
    b.這是另一個 C# 主控台應用程式。 瀏覽至 [應用程式和使用者管理常見工作]，然後按一下 [識別提供者] 索引標籤。
   
    c. 按一下 [新增識別提供者]，然後選取您從 Azure 入口網站下載的中繼資料 XML 檔案。 藉由匯入中繼資料，系統會自動上傳所需的簽章憑證和加密憑證。
   
    ![設定單一登入](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_54.png)
   
    d. 為了在 SAML 要求中包含**判斷提示取用者服務 URL**，請選取 [包含判斷提示取用者服務 URL]。
   
    e. 按一下 [啟用單一登入]。
   
    f. 儲存您的變更。
   
    g. 按一下 [我的系統] 索引標籤。
   
    ![設定單一登入](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_52.png)
   
    h. 將您從 Azure 入口網站複製的「SAML 單一登入服務 URL」貼到 [Azure AD 登入 URL] 文字方塊中。
   
    ![設定單一登入](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_53.png)
   
    i. 透過選取 [手動選取識別提供者]，指定員工是否可以在以使用者識別碼和密碼登入或 SSO 之間進行手動選擇。
   
    j. 在 [SSO URL] 區段中，指定員工應用來登入系統的 URL。 
    在 [傳送給員工的 URL] 下拉式清單中，您可以在下列選項之間做選擇︰
   
    **非 SSO URL**
   
    系統只會傳送一般系統 URL 給員工。 員工無法使用 SSO 來登入，而是必須改為使用密碼或憑證。
   
    **SSO URL** 
   
    系統只會傳送 SSO URL 給員工。 員工可以使用 SSO 來登入。 驗證要求會透過 IdP 重新導向。
   
    **自動選取**
   
    如果未啟用 SSO，系統會傳送一般系統 URL 給員工。 如果已啟用 SSO，系統會檢查員工是否有密碼。 如果有密碼，便會將 SSO URL 和非 SSO URL 傳送給員工。 但如果員工沒有密碼，則只會傳送 SSO URL 給員工。
   
    k. 儲存您的變更。

> [!TIP]
> 現在，當您設定此應用程式時，在 [Azure 入口網站](https://portal.azure.com)內即可閱讀這些指示的簡要版本！  從 [Active Directory] > [企業應用程式] 區段新增此應用程式之後，只要按一下 [單一登入] 索引標籤，即可透過底部的 [組態] 區段存取內嵌的文件。 您可以從以下連結閱讀更多有關內嵌文件功能的資訊：[Azure AD 內嵌文件]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>建立 Azure AD 測試使用者

本節的目標是要在 Azure 入口網站中建立一個名為 Britta Simon 的測試使用者。

   ![建立 Azure AD 測試使用者][100]

**若要在 Azure AD 中建立測試使用者，請執行下列步驟：**

1. 在 Azure 入口網站的左窗格中，按一下 [Azure Active Directory] 按鈕。

    ![Azure Active Directory 按鈕](./media/active-directory-saas-sapbusinessbydesign-tutorial/create_aaduser_01.png)

2. 若要顯示使用者清單，請移至 [使用者和群組]，然後按一下 [所有使用者]。

    ![[使用者和群組] 與 [所有使用者] 連結](./media/active-directory-saas-sapbusinessbydesign-tutorial/create_aaduser_02.png)

3. 若要開啟 [使用者] 對話方塊，按一下 [所有使用者] 對話方塊頂端的 [新增]。

    ![[新增] 按鈕](./media/active-directory-saas-sapbusinessbydesign-tutorial/create_aaduser_03.png)

4. 在 [使用者] 對話方塊中，執行下列步驟：

    ![[使用者] 對話方塊](./media/active-directory-saas-sapbusinessbydesign-tutorial/create_aaduser_04.png)

    a. 在 [名稱] 方塊中，輸入 **BrittaSimon**。

    b. 在 [使用者名稱] 方塊中，輸入使用者 Britta Simon 的電子郵件地址。

    c. 選取 [顯示密碼] 核取方塊，然後記下 [密碼] 方塊中顯示的值。

    d. 按一下 [建立] 。
 
### <a name="create-an-sap-business-bydesign-test-user"></a>建立 SAP Business ByDesign 測試使用者

在本節中，您要在 SAP Business ByDesign 中建立名為 Britta Simon 的使用者。 請與 [SAP Business ByDesign 用戶端支援小組](https://www.sap.com/products/cloud-analytics.support.html)合作，以在 SAP Business ByDesign 平台中新增使用者。 

> [!NOTE]
> 請確定 NameID 值符合 SAP Business ByDesign 平台中的使用者名稱欄位。

### <a name="assign-the-azure-ad-test-user"></a>指派 Azure AD 測試使用者

在本節中，您會將 SAP Business ByDesign 的存取權授與 Britta Simon，讓她能夠使用 Azure 單一登入。

![指派使用者角色][200] 

**若要將 Britta Simon 指派到 SAP Business ByDesign，請執行下列步驟：**

1. 在 Azure 入口網站中，開啟應用程式檢視，接著瀏覽至目錄檢視並移至 [企業應用程式]，然後按一下 [所有應用程式]。

    ![指派使用者][201] 

2. 在應用程式清單中，選取 [SAP Business ByDesign] 。

    ![應用程式清單中的 SAP Business ByDesign 連結](./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_sapbusinessbydesign_app.png)  

3. 在左側功能表中，按一下 [使用者和群組]。

    ![[使用者和群組] 連結][202]

4. 按一下 [新增] 按鈕。 然後選取 [新增指派] 對話方塊上的 [使用者和群組]。

    ![[新增指派] 窗格][203]

5. 在 [使用者和群組] 對話方塊上，選取 [使用者] 清單中的 [Britta Simon]。

6. 按一下 [使用者和群組] 對話方塊上的 [選取] 按鈕。

7. 按一下 [新增指派] 對話方塊上的 [指派] 按鈕。
    
### <a name="test-single-sign-on"></a>測試單一登入

在本節中，您會使用存取面板來測試您的 Azure AD 單一登入設定。

當您在存取面板中按一下 [SAP Business ByDesign ] 圖格時，應該會自動登入您的 SAP Business ByDesign 應用程式。

## <a name="additional-resources"></a>其他資源

* [如何與 Azure Active Directory 整合 SaaS 應用程式的教學課程清單](active-directory-saas-tutorial-list.md)
* [什麼是搭配 Azure Active Directory 的應用程式存取和單一登入？](active-directory-appssoaccess-whatis.md)

<!--Image references-->

[1]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-sapbusinessbydesign-tutorial/tutorial_general_203.png


