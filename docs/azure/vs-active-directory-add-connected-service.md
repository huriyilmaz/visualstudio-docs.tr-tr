---
title: Active Directory bağlı hizmetini kullanma (Visual Studio)
description: Visual Studio bağlı hizmetleri ekle iletişim kutusunu kullanarak Azure Active Directory ekleme
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.custom: devx-track-csharp, aaddev, vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/14/2021
ms.author: ghogen
ms.openlocfilehash: b5ec1c10263fb327a7796950817a3fdef8893729
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386760"
---
# <a name="add-an-azure-active-directory-by-using-connected-services-in-visual-studio"></a>Visual Studio bağlı hizmetleri kullanarak Azure Active Directory ekleme

Azure Active Directory (Azure AD) kullanarak, web apı hizmetlerinde ASP.NET MVC web uygulamaları için tek Sign-On (SSO) veya Active Directory kimlik doğrulamasını destekleyebilirsiniz. Azure AD kimlik doğrulaması ile kullanıcılarınız, web uygulamalarınıza bağlanmak için Azure Active Directory hesaplarını kullanabilir. Web API 'si ile Azure AD kimlik doğrulamasının avantajları, bir Web uygulamasından API 'YI kullanıma sunmadan gelişmiş veri güvenliği içerir. Azure AD ile ayrı bir kimlik doğrulama sistemini kendi hesabı ve Kullanıcı yönetimi ile yönetmeniz gerekmez.

bu makale ve yardımcı makaleler, Active Directory için Visual Studio bağlı hizmet özelliğini kullanma hakkında ayrıntılı bilgi sağlar. yetenek Visual Studio 2015 ve üzeri sürümlerde kullanılabilir.

Active Directory bağlı hizmet, ASP.NET Core uygulamalarını desteklemez.

## <a name="prerequisites"></a>Önkoşullar

- azure hesabı: bir azure hesabınız yoksa, [ücretsiz deneme için kaydolabilir](https://azure.microsoft.com/pricing/free-trial/?WT.mc_id=A261C142F) veya [Visual Studio abone avantajlarınızı etkinleştirebilirsiniz](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F).
- **Visual Studio 2015** veya üzeri. [Visual Studio şimdi indirin](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).

### <a name="connect-to-azure-active-directory-using-the-connected-services-dialog"></a>bağlı hizmetler iletişim kutusunu kullanarak Azure Active Directory Bağlan

1. Visual Studio, bir ASP.NET MVC projesi veya ASP.NET Web apı projesi oluşturun veya açın. MVC, Web API, Single-Page uygulaması, Azure API uygulaması, Azure mobil uygulaması ve Azure mobil hizmet şablonları kullanabilirsiniz.

1. **Project > bağlı hizmet ekle...** menü komutunu seçin veya Çözüm Gezgini projenin altında bulunan **bağlı hizmetler** düğümüne çift tıklayın.

1. **Bağlı hizmetler** sayfasında, **Azure Active Directory kimlik doğrulaması**' nı seçin.

    ![Bağlı hizmetler sayfası](./media/vs-azure-active-directory/connected-services-add-active-directory.png)

1. **Giriş** sayfasında, **İleri**' yi seçin. bu sayfada hata görürseniz, [Azure Active Directory bağlı hizmeti ile hataları tanılama](vs-active-directory-error.md)bölümüne bakın.

    ![Giriş sayfası](./media/vs-azure-active-directory/configure-azure-ad-wizard-1.png)

1. **Çoklu oturum açma** sayfasında, **etki alanı** açılır listesinden bir etki alanı seçin. liste, Visual Studio hesap Ayarlar iletişim kutusunda listelenen hesaplar tarafından erişilebilen tüm etki alanlarını içerir (**dosya > hesap Ayarlar...**). Alternatif olarak, aradığınız birini bulamazsanız bir etki alanı adı girebilirsiniz `mydomain.onmicrosoft.com` . Azure Active Directory bir uygulama oluşturma veya var olan bir Azure Active Directory uygulamasındaki ayarları kullanma seçeneğini belirleyebilirsiniz. Bittiğinde **İleri ' yi** seçin.

    ![Çoklu oturum açma sayfası](./media/vs-azure-active-directory/configure-azure-ad-wizard-2.png)

1. **Dizin erişimi** sayfasında, istediğiniz şekilde **Dizin verilerini oku** seçeneğini belirleyin. Geliştiriciler genellikle bu seçeneği içerir.

    ![Dizin erişimi sayfası](./media/vs-azure-active-directory/configure-azure-ad-wizard-3.png)

1. Azure AD kimlik doğrulamasını etkinleştirmek üzere projenizde değişiklikler başlatmak için **son** ' u seçin. Visual Studio şu süre boyunca ilerleme gösterir:

    ![Bağlı hizmet ilerlemesini Active Directory](./media/vs-azure-active-directory/active-directory-connected-service-output.png)

1. işlem tamamlandığında, Visual Studio tarayıcınızı, proje türüne uygun olarak aşağıdaki makalelerden birine açar:

    - [.NET MVC projelerini kullanmaya başlama](vs-active-directory-dotnet-getting-started.md)
    - [.NET WebAPI projelerini kullanmaya başlama](vs-active-directory-webapi-getting-started.md)

1. Ayrıca, [Azure portal](https://go.microsoft.com/fwlink/p/?LinkID=525040)Active Directory etki alanını da görebilirsiniz.

## <a name="how-your-project-is-modified"></a>Projenizin nasıl değiştirildiği

bağlı hizmet sihirbazı eklediğinizde, Visual Studio projenize Azure Active Directory ve ilişkili başvuruları ekler. Projenizdeki yapılandırma dosyaları ve kod dosyaları da Azure AD desteği eklemek için değiştirilir. Visual Studio yapılan belirli değişiklikler proje türüne bağlıdır. Ayrıntılar için aşağıdaki makalelere bakın:

- [.NET MVC projeme ne oldu?](vs-active-directory-dotnet-what-happened.md)
- [Web API projem ne oldu?](vs-active-directory-webapi-what-happened.md)

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization)
- [Microsoft 'a ASP.NET web uygulamasına oturum açma ekleme](/azure/active-directory/develop/quickstart-v2-aspnet-webapp)