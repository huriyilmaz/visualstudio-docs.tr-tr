---
title: Birden çok kullanıcı hesabıyla çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9aa08d68da53f54491439da8e35c28db90f4c508
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662667"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden çok Microsoft hesabınız ve/veya iş veya okul hesabınız varsa, bu kaynakları ayrı olarak oturum açmanıza gerek kalmadan herhangi bir hesaptan erişebilmek için, tümünü Visual Studio 'ya ekleyebilirsiniz. Visual Studio 2015 RTM tarihinde Tarih, Azure, Application Insights, Team Foundation Server ve Office 365 Hizmetleri, kolaylaştırılmış oturum açma deneyimini destekler. Zaman içinde diğer hizmetler kullanılabilir hale gelebilir.

 Bir makineye birden çok hesap ekledikten sonra, başka bir makinede Visual Studio 'da oturum açarsanız, bu hesap kümesi sizinle dolaşımda olur. Hesap adları dolaşımda değil, kimlik bilgilerinin olmasa da emin olmak önemlidir. Bu nedenle, yeni makinede kaynaklarını ilk kez kullanmaya çalıştığınızda diğer hesapların kimlik bilgilerini girmeniz istenir.

 Bu izlenecek yol, Visual Studio 'ya birden çok hesap eklemeyi ve bu hesaplardan erişilebilen kaynakların **bağlı hizmet ekle** iletişim kutusu, **Sunucu Gezgini**ve **Takım Gezgini** gibi yerlerde nasıl yansıtıldığını gösterir. .

#### <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

1. Microsoft hesabı veya kurumsal hesapla Visual Studio 2015 ' de oturum açın. Kullanıcı adınızı pencerenin sağ üst köşesine yansımış ve şuna benzer şekilde görmeniz gerekir:

     ![Currentlly oturum açan Kullanıcı](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Sunucu Gezgini Azure hesabınıza erişin
 **Sunucu Gezgini**açmak için **CTRL + ALT + S** tuşlarına basın. Azure simgesine tıklayın ve genişletildiğinde, Visual Studio 2015 ' de oturum açmak için kullandığınız KIMLIKLE ilişkili Azure hesabında kullanılabilir kaynakları görmeniz gerekir. Bu, Mr. Gudo değil, kendi kaynaklarınızı görmeniz dışında şuna benzer görünmelidir:

 ![Genişletilmiş Azure araçları düğümünü gösteren Sunucu Gezgini](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 Belirli bir cihazda Visual Studio 'Yu ilk kez kullandığınızda, iletişim kutusunda yalnızca IDE 'de oturum açtığınız KIMLIğIN altına kaydedilen abonelikler gösterilir. Azure düğümüne sağ tıklayıp, **abonelikleri Yönet ve filtrele** ' yi seçip hesap Seçicisi denetiminden hesaplarınızı ekleyerek, diğer hesaplarınızdan herhangi birine ait kaynaklara doğrudan **Sunucu Gezgini** erişebilirsiniz. İsterseniz aşağı oka tıklayıp hesaplar listesinden seçerek başka bir hesap seçebilirsiniz. Hesabı seçtikten sonra, bu hesap altında Sunucu Gezgini hangi abonelikleri göstermek istediğinizi seçebilirsiniz.

 ![Azure aboneliklerini yönetme iletişim kutusu](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 Sunucu Gezgini bir sonraki açışınızda, bu abonelikler için kaynaklar görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişin

1. İçinde C#bir evrensel uygulama projesi oluşturun.

2. Çözüm Gezgini ' de proje düğümüne sağ tıklayın ve **> bağlı hizmet ekle**' yi seçin. Bağlı hizmet Ekle Sihirbazı görüntülenir ve Azure hesabındaki, Visual Studio oturum açma KIMLIĞINIZLE ilişkili hizmetlerin listesini gösterir. Azure 'da ayrı olarak oturum açmanız gerekmediğini unutmayın. Ancak, belirli bir bilgisayardan kaynaklarına ilk kez erişmeye çalıştığınızda diğer hesaplarda oturum açmanız gerekir.

    > [!WARNING]
    > Visual Studio 2015 ' de belirli bir bilgisayarda ilk kez bir mağaza uygulaması oluşturuyorsanız, **Ayarlar &#124; ' a giderek cihazınızı geliştirme modu için etkinleştirmeniz istenir. Bilgisayarınızdaki geliştiriciler için &#124; güncelleştirmeler ve güvenlik** . Daha fazla bilgi için bkz. [cihazınızı geliştirme Için etkinleştirme](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access_azure"></a>Web projesindeki Azure Active Directory erişim
 Azure AD, ASP.NET MVC web uygulamalarında Son Kullanıcı çoklu oturum açma desteği veya Web API hizmetlerinde AD kimlik doğrulaması desteği sunar. Etki alanı kimlik doğrulaması, bireysel kullanıcı hesabı kimlik doğrulamasından farklıdır; Active Directory etki alanına erişimi olan kullanıcılar, Web uygulamalarınıza bağlanmak için mevcut Azure AD hesaplarını kullanabilir. Office 365 uygulamaları, etki alanı kimlik doğrulaması da kullanabilir. Bunu eylemde görmek için, bir Web uygulaması oluşturun (**dosya > yeni proje > C# > bulut > ASP.NET Web uygulaması**). Yeni ASP.NET projesi iletişim kutusunda **kimlik doğrulamasını Değiştir**' i seçin. Kimlik doğrulama Sihirbazı görünür ve uygulamanızda kullanılacak kimlik doğrulaması türünü seçmenizi sağlar.

 ![ASP.NET için kimlik doğrulama iletişim kutusunu değiştirme](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 ASP.NET ' de farklı kimlik doğrulama türleri hakkında daha fazla bilgi için, bkz. [Visual Studio 2013 Web projeleri oluşturma](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (kimlik doğrulama hakkındaki bilgiler hala Visual Studio 2015 için geçerlidir).

### <a name="access-your-visual-studio-team-services-account"></a>Visual Studio Team Services hesabınıza erişin
 Ana menüden **takım > Team Foundation Server Connect** ' i seçerek **Takım Gezgini** penceresini açın. **Takım projelerini Seç**' e tıklayın ve ardından **Team Foundation Server seçin**' in altındaki liste kutusunda, Visual Studio Team Services hesabınızın URL 'sini görmeniz gerekir. URL 'YI seçtiğinizde, kimlik bilgilerinizi yeniden girmeniz gerekmeden oturumunuz açılır.

## <a name="add-a-second-user-account-to-visual-studio"></a>Visual Studio 'ya ikinci bir kullanıcı hesabı ekleme
 Visual Studio 'nun sağ üst köşesindeki Kullanıcı adınızın yanındaki aşağı oka tıklayın. Ardından **Hesap ayarları** menü öğesine tıklayın. **Hesap Yöneticisi** iletişim kutusu görünür ve oturum açtığınız hesabı görüntüler. Yeni bir Microsoft hesabı veya yeni bir iş veya okul hesabı eklemek için iletişim kutusunun sol alt köşesindeki **Hesap Ekle** bağlantısına tıklayın.

 ![Visual Studio hesap Seçicisi](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Yeni hesap kimlik bilgilerini girmek için istemleri izleyin. Aşağıdaki çizimde, bir Kullanıcı Contoso.com iş hesabını ekledikten sonra Hesap Yöneticisi gösterilmektedir.

 ![Hesap Yöneticisi](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Bağlı hizmetler Ekleme Sihirbazı 'Nı yeniden ziyaret edin Sunucu Gezgini
 Şimdi **Sunucu Gezgini** yeniden gidin, Azure düğümüne sağ tıklayıp **abonelikleri Yönet ve filtrele**' yi seçin. Geçerli hesabın yanındaki aşağı açılan oka tıklayarak yeni hesabı seçin ve ardından Sunucu Gezgini hangi abonelikleri göstermek istediğinizi seçin. Belirtilen abonelikle ilişkili tüm hizmetleri görmeniz gerekir. Visual Studio IDE 'de Şu anda ikinci hesapla oturum açmış olsanız da bu hesabın Hizmetleri ve kaynaklarında oturum açtınız. Aynı değer, **proje > bağlı hizmet ekleme** ve **Takım > Team Foundation Server 'e bağlanması**için de geçerlidir.
