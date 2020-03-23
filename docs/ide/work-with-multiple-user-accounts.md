---
title: Birden çok kullanıcı hesabıyla çalışma
ms.date: 07/23/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872089158b6e4dc0b55c26ad187e3b68d0501f26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027603"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma

Birden fazla Microsoft hesabınız ve/veya iş veya okul hesabınız varsa, ayrı olarak oturum açmanız gerekmeden herhangi bir hesaptan kaynaklara erişebilmeniz için bunların tümlerini Visual Studio'ya ekleyebilirsiniz. Azure, Uygulama Öngörüleri, Azure DevOps ve Office 365 hizmetlerinin tümü kolaylaştırılmış oturum açma deneyimini destekler.

Bir makineye birden fazla hesap ekledikten sonra, visual studio'da başka bir makinede oturum açsanız bu hesap kümesi sizinle birlikte dolaşır.

> [!NOTE]
> Hesap adları dolaşımda olsa da, kimlik bilgileri yok. Kaynaklarını yeni bir makinede ilk kez kullanmaya çalıştığınızda, bu diğer hesaplar için kimlik bilgilerini girmeniz istenir.

Bu makalede, Visual Studio'ya birden çok hesap nasıl ekleyeceğiniz gösterilmektedir. Ayrıca, **Bağlı Hizmet Ekle** iletişim kutusu, Sunucu **Gezgini**ve **Takım Gezgini**gibi yerlerde bu hesaplardan erişilebilen kaynakları nasıl göreceğinizi de gösterir.

## <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

Visual Studio'da bir Microsoft hesabı veya kuruluş hesabıyla oturum açın. Kullanıcı adınızıpencerenin üst köşesinde aşağıdakine benzer şekilde görmeniz gerekir:

![Şu anda kullanıcı oturum açmış](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Azure hesabınıza Server Explorer'da erişin

Sunucu Gezgini'ni açmak için**Sunucu Gezgini** **Görüntüle'yi** > seçin (veya "Genel" [ortam ayarlarını](../ide/environment-settings.md)kullanıyorsanız **Ctrl**+**Alt**+**S**tuşuna basın). **Azure** düğümini genişletin ve Visual Studio'da oturum açmanız için kullandığınız hesapla ilişkili Azure hesabında bulunan kaynakları içerdiğine dikkat edin. Aşağıdaki resme benzer:

![Azure düğümüile Sunucu Gezgini genişletildi](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Visual Studio'yu herhangi bir cihazda ilk kez kullandığınızda, iletişim kutusu yalnızca oturum açtığunuzun hesabı altında kayıtlı abonelikleri gösterir. Azure **düğümüne** sağ tıklayarak, **Abonelikleri Yönet ve Filtrele'yi**seçerek ve hesap seçici denetiminden hesaplarınızı ekleyerek diğer hesaplarınız için kaynaklara doğrudan **Server Explorer'dan** erişebilirsiniz. Daha sonra aşağı ok tıklayarak ve hesaplar listesinden seçerek, istenirse başka bir hesap seçebilirsiniz. Hesabı seçtikten sonra, sunucu **gezgininde**görüntülenecek bu hesabın altındaki abonelikleri özelleştirebilirsiniz.

![Azure Abonelikleri iletişim kutusunu yönetme](../ide/media/vs2015_manage_subs.png)

**Server Explorer'ı**bir sonraki açtığınızda, bu aboneliğin kaynakları görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı Hizmet Ekle iletişim kutusu yla Azure hesabınıza erişin

1. Varolan bir projeyi açın veya yeni bir proje oluşturun.

1. **Çözüm Gezgini'nde**proje düğümünden birini seçin ve sonra sağ tıklatın ve**Bağlı Hizmet** **Ekle'yi** > seçin.

   **Bağlı Hizmet Ekle** sihirbazı görüntülenir ve Azure hesabında Visual Studio kişiselleştirme hesabınızla ilişkili hizmetlerin listesini gösterir. Azure'da ayrı oturum açmanız gerekmez. Ancak, kaynaklarına farklı bir makineden ilk kez erişmeye çalıştığınızda diğer hesaplarda oturum açmanız gerekir.

### <a name="access-azure-active-directory-in-a-web-project"></a>Web projesinde Azure Etkin Dizine erişin

Azure Active Directory (AAD), web API hizmetlerinde MVC web uygulamaları veya AD kimlik doğrulaması ASP.NET son kullanıcı tek oturum açma desteği sağlar. Etki alanı kimlik doğrulaması, tek tek kullanıcı hesabı kimlik doğrulamasından farklıdır. Etkin Dizin etki alanınıza erişimi olan kullanıcılar, web uygulamalarınıza bağlanmak için mevcut AAD hesaplarını kullanabilir. Office 365 uygulamaları etki alanı kimlik doğrulamasını da kullanabilir.

::: moniker range="vs-2017"

Bunu iş başında görmek için, yeni bir **ASP.NET Core Web Application** projesi oluşturun. Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunda, **Web Uygulaması** şablonunu seçin ve ardından **Kimlik Doğruluğunu Değiştir'i**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

Bunu iş başında görmek için, yeni bir **ASP.NET Core Web Application** projesi oluşturun. Yeni **bir ASP.NET Çekirdek Web Uygulaması Oluştur** sayfasında, Web **Uygulaması** şablonunu seçin ve ardından **Kimlik Doğrulama**altında **Değiştir'i** seçin.

::: moniker-end

**Kimlik Doğrulamasını Değiştir** iletişim kutusu, uygulamanızda ne tür kimlik doğrulaması kullanacağınızı seçebileceğiniz görünür.

![kimlik doğrulama iletişim kutusunu ASP.NET için değiştirme](../ide/media/vs2015_change_authentication.png)

ASP.NET'daki farklı kimlik doğrulama türleri hakkında daha fazla bilgi için [Visual Studio'da ASP.NET web projeleri oluştur'a](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods)bakın.

### <a name="access-your-azure-devops-organization"></a>Azure DevOps kuruluşunuza erişin

Ana menüden, Team Explorer - Connect penceresini açmak**için** **Bağlantıları Yönet ekibi'ni** > seçin. **Team Explorer - Connect** **Bağlantıları** > **Yönet'i**seçin Projeye bağlanın. Projeye **Bağlan** iletişim kutusunda, listeden bir proje seçin (veya **TFS Sunucusu Ekle'yi** seçin ve URL'yi sunucunuza girin). Bir URL seçtiğinizde, kimlik bilgilerinizi yeniden girmenize gerek kalmadan oturum açmış oluyorsunuz.

Daha fazla bilgi için Bkz. [Takım Gezgini'ndeki projelere bağlanın.](connect-team-project.md)

## <a name="add-an-additional-account-to-visual-studio"></a>Visual Studio'ya ek hesap ekleme

Visual Studio'ya ek bir hesap eklemek için:

1. **Dosya** > **Hesabı Ayarlarını**seçin.

1. **Tüm Hesaplar**altında **hesap ekle'yi**seçin.

1. Hesap **sayfanızda Oturum Aç'ta** hesabı seçin veya **başka bir hesap kullan'ı**seçin. Yeni hesap kimlik bilgilerini girmek için istemleri izleyin.

(İsteğe bağlı) Artık **Server Explorer'a** gidebilir ve az önce eklediğiniz hesapla ilişkili Azure hizmetlerini görebilirsiniz. **Sunucu Gezgini'nde,** **Azure** düğümüne sağ tıklayın ve **Abonelikleri Yönet ve Filtrele'yi**seçin. Geçerli hesabın yanındaki açılır oka tıklayarak yeni hesabı seçin ve ardından **Server Explorer'da**görüntülemek istediğiniz abonelikleri seçin. Belirtilen abonelikle ilişkili tüm hizmetleri görmeniz gerekir. Şu anda Visual Studio'da ikinci hesapla oturum açmamış olsanız da, bu hesabın hizmetlerinde ve kaynaklarında oturum açmış sınız. Aynı durum **Project** > **Add Connected Service** ve **Team** > **Connect to Team Foundation Server**için de geçerlidir.

### <a name="add-an-account-using-device-code-flow"></a>Aygıt kodu akışını kullanarak hesap ekleme

Bazı durumlarda, düzenli olarak oturum açamaz veya hesap ekemezsiniz. Bu durum, Internet Explorer herhangi bir nedenle engellenirse veya ağınız bir güvenlik duvarının arkasındaysa gerçekleşebilir. Bunu çözmek için, bir hesap eklemek veya hesabınızı yeniden doğrulamak için *aygıt kodu akışını* etkinleştirebilirsiniz. Aygıt kodu akışı, farklı bir tarayıcı kullanarak veya&mdash;farklı bir makinede fiziksel veya sanal (VM) oturum açmanızı sağlar.

Aygıt kodu akışını kullanarak oturum açma:

1.  >  **Araçlar****Options**Seçenekleri > **Ortamı**altında [**Hesaplar**](reference/accounts-environment-options-dialog-box.md) sayfasını açın ve ardından bir **hesap eklerken veya yeniden kimlik doğrularken aygıt kodu akışını etkinleştir'i**seçin. Seçenekler sayfalarını kapatmak için **Tamam'ı** seçin.

1. Hesap yönetimi sayfasını açmak için **Dosya** > **Hesabı Ayarları'nı** seçin.

1. **Tüm Hesaplar**altında **hesap ekle'yi** seçin.

   İletişim kutusu, bir URL ve bir web tarayıcısına yapıştırılabilmek için bir kod gösterir.

   ![Aygıt kodu akışı URL'si ve kodu](media/work-with-multiple-user-accounts/device-login-code.png)

1. İletişim kutusunun metnini kopyalamak için **Ctrl**+**C** tuşuna basın ve ardından iletişim kutusunu kapatmak için **Tamam'ı** seçin. Kopyaladığınız metni Not Defteri gibi bir metin düzenleyicisine yapıştırın. Bu, kodun bir sonraki adımda kopyalatmasını kolaylaştırır.

1. Visual Studio'da oturum açmak için kullanmak istediğiniz makine veya web tarayıcısında cihaz giriş URL'sine gidin ve ardından kod **yazan**kutuya kopyaladığınız kodu yapıştırın veya girin.

   **Visual Studio** uygulama adı sayfada daha aşağı görünmelidir.

1. **Visual Studio**altında, **Devam'ı**seçin.

   ![cihaz-giriş-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Hesap kimlik bilgilerinizi girmek için istemleri izleyin.

   Cihazınızda Visual Studio'da oturum girdiğinizi ve tarayıcı penceresini kapatabileceğinizi söyleyen bir sayfa görüntülenir.

   ![Visual Studio tarayıcı tamamlandı oturum açma](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Visual Studio'daki hesap yönetimi sayfasına geri döndüğünüzde, Tüm **Hesaplar**altında listelenen yeni eklenen hesabı görürsünüz. **Kapat'ı**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio'da oturum açın](/visualstudio/mac/signing-in)
