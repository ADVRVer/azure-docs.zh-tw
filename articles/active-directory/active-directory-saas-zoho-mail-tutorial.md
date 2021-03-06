---
title: "教學課程：Azure Active Directory 與 Zoho 整合 | Microsoft Docs"
description: "了解如何設定 Azure Active Directory 與 Zoho 之間的單一登入。"
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 9874e1f3-ade5-42e7-a700-e08b3731236a
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/24/2017
ms.author: jeedes
ms.translationtype: HT
ms.sourcegitcommit: 74b75232b4b1c14dbb81151cdab5856a1e4da28c
ms.openlocfilehash: f0688cb75584ada805b944d2ef5409d66ab37339
ms.contentlocale: zh-tw
ms.lasthandoff: 07/26/2017

---
# <a name="tutorial-azure-active-directory-integration-with-zoho"></a>教學課程：Azure Active Directory 與 Zoho 整合

在本教學課程中，您會了解如何將 Zoho 與 Azure Active Directory (Azure AD) 進行整合。

Zoho 與 Azure AD 整合提供下列優點：

- 您可以在 Azure AD 中控制可存取 Zoho 的人員。
- 您可以讓使用者使用他們的 Azure AD 帳戶自動登入 Zoho (單一登入)。
- 您可以在 Azure 入口網站中集中管理您的帳戶。

如果您想要了解有關 SaaS 應用程式與 Azure AD 之整合的更多詳細資料，請參閱[什麼是搭配 Azure Active Directory 的應用程式存取和單一登入](active-directory-appssoaccess-whatis.md)。

## <a name="prerequisites"></a>必要條件

若要設定 Azure AD 與 Zoho 整合，您需要下列項目：

- Azure AD 訂用帳戶
- 已啟用 Zoho 單一登入的訂用帳戶

> [!NOTE]
> 若要測試本教學課程中的步驟，我們不建議使用生產環境。

若要測試本教學課程中的步驟，您應該遵循這些建議：

- 除非必要，否則請勿使用生產環境。
- 如果您沒有 Azure AD 試用環境，您可以[取得一個月試用](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>案例描述
在本教學課程中，您會在測試環境中測試 Azure AD 單一登入。 本教學課程中說明的案例由二個主要建置組塊組成：

1. 從資源庫新增 Zoho
2. 設定並測試 Azure AD 單一登入

## <a name="adding-zoho-from-the-gallery"></a>從資源庫新增 Zoho
若要設定將 Zoho 整合到 Azure AD 中，您需要從資源庫將 Zoho 新增到受管理的 SaaS 應用程式清單。

**若要從資源庫加入 Zoho，請執行下列步驟：**

1. 在 **[Azure 入口網站](https://portal.azure.com)**的左方瀏覽窗格中，按一下 [Azure Active Directory] 圖示。 

    ![Azure Active Directory 按鈕][1]

2. 瀏覽至 [企業應用程式]。 然後移至 [所有應用程式]。

    ![企業應用程式刀鋒視窗][2]
    
3. 若要新增新的應用程式，請按一下對話方塊頂端的 [新增應用程式] 按鈕。

    ![新增應用程式按鈕][3]

4. 在搜尋方塊中，輸入 **Zoho**，從結果面板中選取 [Zoho]，然後按一下 [新增] 按鈕以新增應用程式。

    ![結果清單中的 Zoho](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>設定和測試 Azure AD 單一登入

在本節中，您會以名為 "Britta Simon" 的測試使用者身分，使用 Zoho 設定及測試 Azure AD 單一登入。

若要讓單一登入運作，Azure AD 必須知道 Zoho 與 Azure AD 中互相對應的使用者。 換句話說，必須建立 Azure AD 使用者和 Zoho 中相關使用者之間的連結關聯性。

在 Zoho 中，將 Azure AD 中**使用者名稱**的值，指派為 **Username** 的值，以建立連結關聯性。

若要設定及測試與 Zoho 搭配運作的 Azure AD 單一登入，您需要完成下列構成要素：

1. **[設定 Azure AD 單一登入](#configure-azure-ad-single-sign-on)** - 讓您的使用者能夠使用此功能。
2. **[建立 Azure AD 測試使用者](#create-an-azure-ad-test-user)** - 使用 Britta Simon 測試 Azure AD 單一登入。
3. **[建立 Zoho 測試使用者](#create-a-zoho-test-user)** - 使 Zoho 中對應的 Britta Simon 連結到該使用者在 Azure AD 中的代表項目。
4. **[指派 Azure AD 測試使用者](#assign-the-azure-ad-test-user)** - 讓 Britta Simon 能夠使用 Azure AD 單一登入。
5. **[測試單一登入](#test-single-sign-on)**，驗證組態是否能運作。

### <a name="configure-azure-ad-single-sign-on"></a>設定 Azure AD 單一登入

在本節中，您會在 Azure 入口網站中啟用 Azure AD 單一登入，然後在您的 Zoho 應用程式中設定單一登入。

**若要使用 Zoho 設定 Azure AD 單一登入，請執行下列步驟：**

1. 在 Azure 入口網站的 [Zoho] 應用程式整合頁面上，按一下 [單一登入]。

    ![設定單一登入連結][4]

2. 在 [單一登入] 對話方塊上，於 [模式] 選取 [SAML 登入]，以啟用單一登入。
 
    ![單一登入對話方塊](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_samlbase.png)

3. 在 [Zoho 網域與 URL] 區段中，執行下列步驟：

    ![Zoho 網域與 URL 單一登入資訊](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_url.png)

    a. 在 [登入 URL] 文字方塊中，使用下列模式輸入 URL︰`https://<company name>.zohomail.com`

    > [!NOTE] 
    > 這不是真實的值。 請使用實際的登入 URL 來更新此值。 請連絡 [Zoho 客戶支援小組](https://www.zoho.com/mail/contact.html)以取得此值。 
 
4. 在 [SAML 簽署憑證] 區段上，按一下 [憑證 (Base64)]，然後將憑證檔案儲存在您的電腦上。

    ![憑證下載連結](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_certificate.png) 

5. 按一下 [儲存]  按鈕。

    ![設定單一登入儲存按鈕](./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_400.png)

6. 在 [Zoho 組態] 區段上，按一下 [設定 Zoho] 以開啟 [設定登入] 視窗。 從 [快速參考] 區段中複製「登出 URL」、「變更密碼 URL」及「SAML 單一登入服務 URL」。

    ![Zoho 組態](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_configure.png) 

7. 在不同的 Web 瀏覽器視窗中，以系統管理員身分登入您的 Zoho Mail 公司網站。

8. 移至 [控制台] 。
   
    ![控制台](./media/active-directory-saas-zoho-mail-tutorial/ic789607.png "控制台")

9. 按一下 [SAML 驗證]  索引標籤。
   
    ![SAML 驗證](./media/active-directory-saas-zoho-mail-tutorial/ic789608.png "SAML 驗證")

10. 在 [SAML 驗證詳細資料]  區段中，執行下列步驟：
   
    ![SAML 驗證詳細資料](./media/active-directory-saas-zoho-mail-tutorial/ic789609.png "SAML 驗證詳細資料")
   
    a. 在 [登入 URL] 文字方塊中，貼上您從 Azure 入口網站複製的 **SAML 單一登入服務 URL**。
   
    b. 在 [登出 URL] 文字方塊中，貼上您從 Azure 入口網站複製的**登出 URL**。
   
    c. 在 [變更密碼 URL] 文字方塊中，貼上您從 Azure 入口網站複製的 [變更密碼 URL]。
       
    d. 在記事本中開啟從 Azure 入口網站下載的 Base-64 編碼憑證，將其內容複製到您的剪貼簿，然後貼到 [PublicKey] 文字方塊中。
   
    e. 選取 [RSA] 做為 [演算法]。
   
    f. 按一下 [確定] 。

> [!TIP]
> 現在，當您設定此應用程式時，在 [Azure 入口網站](https://portal.azure.com)內即可閱讀這些指示的簡要版本！  從 [Active Directory] > [企業應用程式] 區段新增此應用程式之後，只要按一下 [單一登入] 索引標籤，即可透過底部的 [組態] 區段存取內嵌的文件。 您可以從以下連結閱讀更多有關內嵌文件功能的資訊：[Azure AD 內嵌文件]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="create-an-azure-ad-test-user"></a>建立 Azure AD 測試使用者

本節的目標是要在 Azure 入口網站中建立一個名為 Britta Simon 的測試使用者。

   ![建立 Azure AD 測試使用者][100]

**若要在 Azure AD 中建立測試使用者，請執行下列步驟：**

1. 在 Azure 入口網站的左窗格中，按一下 [Azure Active Directory] 按鈕。

    ![Azure Active Directory 按鈕](./media/active-directory-saas-zoho-mail-tutorial/create_aaduser_01.png)

2. 若要顯示使用者清單，請移至 [使用者和群組]，然後按一下 [所有使用者]。

    ![[使用者和群組] 與 [所有使用者] 連結](./media/active-directory-saas-zoho-mail-tutorial/create_aaduser_02.png)

3. 若要開啟 [使用者] 對話方塊，按一下 [所有使用者] 對話方塊頂端的 [新增]。

    ![[新增] 按鈕](./media/active-directory-saas-zoho-mail-tutorial/create_aaduser_03.png)

4. 在 [使用者] 對話方塊中，執行下列步驟：

    ![[使用者] 對話方塊](./media/active-directory-saas-zoho-mail-tutorial/create_aaduser_04.png)

    a. 在 [名稱] 方塊中，輸入 **BrittaSimon**。

    b. 在 [使用者名稱] 方塊中，輸入使用者 Britta Simon 的電子郵件地址。

    c. 選取 [顯示密碼] 核取方塊，然後記下 [密碼] 方塊中顯示的值。

    d. 按一下 [建立] 。
 
### <a name="create-a-zoho-test-user"></a>建立 Zoho 測試使用者

若要讓 Azure AD 使用者可以登入 Zoho Mail，必須將他們佈建到 Zoho Mail。 Zoho Mail 需以手動的方式佈建。

> [!NOTE]
> 您可以使用任何其他的 Zoho Mail 使用者帳戶建立工具或 Zoho Mail 提供的 API，佈建 AAD 使用者帳戶。

### <a name="to-provision-a-user-account-perform-the-following-steps"></a>若要佈建使用者帳戶，請執行下列步驟：

1. 以系統管理員身分登入您的 **Zoho Mail** 公司網站。

2. 移至 [控制台] \> [郵件和文件]。

3. 移至 [使用者詳細資料] \> [新增使用者]。
   
    ![新增使用者](./media/active-directory-saas-zoho-mail-tutorial/ic789611.png "新增使用者")

4. 在 [新增使用者]  對話方塊上，執行下列步驟：
   
    ![新增使用者](./media/active-directory-saas-zoho-mail-tutorial/ic789612.png "新增使用者")
   
    a. 在 [名字] 文字方塊中，輸入使用者的名字，例如 **Britta**。

    b. 在 [姓氏] 文字方塊中，輸入使用者的姓氏，例如 **Simon**。

    c. 在 [電子郵件識別碼] 文字方塊中，輸入像是 **brittasimon@contoso.com** 的使用者電子郵件識別碼。

    d. 在 [密碼] 文字方塊中，輸入使用者的密碼。
   
    e. 按一下 [確定] 。  
      
    > [!NOTE]
    > Azure Active Directory 帳戶的持有者會收到一封包含連結的電子郵件，以在啟用帳戶前進行確認。

### <a name="assign-the-azure-ad-test-user"></a>指派 Azure AD 測試使用者

在本節中，您會將 Zoho 的存取權授與 Britta Simon，讓她能夠使用 Azure 單一登入。

![指派使用者角色][200] 

**若要將 Britta Simon 指派給 Zoho，請執行下列步驟：**

1. 在 Azure 入口網站中，開啟應用程式檢視，接著瀏覽至目錄檢視並移至 [企業應用程式]，然後按一下 [所有應用程式]。

    ![指派使用者][201] 

2. 在應用程式清單中，選取 [Zoho]。

    ![應用程式清單中的 Zoho 連結](./media/active-directory-saas-zoho-mail-tutorial/tutorial_zoho_app.png)  

3. 在左側功能表中，按一下 [使用者和群組]。

    ![[使用者和群組] 連結][202]

4. 按一下 [新增] 按鈕。 然後選取 [新增指派] 對話方塊上的 [使用者和群組]。

    ![[新增指派] 窗格][203]

5. 在 [使用者和群組] 對話方塊上，選取 [使用者] 清單中的 [Britta Simon]。

6. 按一下 [使用者和群組] 對話方塊上的 [選取] 按鈕。

7. 按一下 [新增指派] 對話方塊上的 [指派] 按鈕。
    
### <a name="test-single-sign-on"></a>測試單一登入

在本節中，您會使用存取面板來測試您的 Azure AD 單一登入設定。

當您在存取面板中按一下 [Zoho] 圖格時，應該會自動登入您的 Zoho 應用程式。
如需「存取面板」的詳細資訊，請參閱[存取面板簡介](active-directory-saas-access-panel-introduction.md)。 

## <a name="additional-resources"></a>其他資源

* [如何與 Azure Active Directory 整合 SaaS 應用程式的教學課程清單](active-directory-saas-tutorial-list.md)
* [什麼是搭配 Azure Active Directory 的應用程式存取和單一登入？](active-directory-appssoaccess-whatis.md)



<!--Image references-->

[1]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-zoho-mail-tutorial/tutorial_general_203.png


