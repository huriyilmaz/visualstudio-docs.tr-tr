---
title: Birden çok kullanıcı hesabıyla çalışma
description: Herhangi bir hesaptan kaynaklara ayrı olarak oturum Visual Studio için tüm Microsoft hesaplarınızı Visual Studio hesaplara nasıl ekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ae6a91d5df31b5ee154b4074b5661bd36f3ade61
ms.sourcegitcommit: bfae1f88c278835e26f3200cfced769be3191fc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2021
ms.locfileid: "132535301"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma

Birden çok Microsoft hesabınız ve/veya iş veya okul hesabınız varsa Visual Studio, kaynaklarda ayrı olarak oturum açmanıza gerek kalmadan herhangi bir hesaptan kaynaklara erişebilirsiniz. Azure, Uygulama Analizler, Azure DevOps ve Microsoft 365 hizmetlerinin hepsi kolaylaştırılmış oturum açma deneyimini destekler.

Bir makineye birden çok hesap eklemenizin ardından, başka bir makinede oturum alasanız bu hesap Visual Studio birlikte dolar.

> [!NOTE]
> Hesap adları dolasa da kimlik bilgileri dolanmaz. Kaynaklarını yeni bir makinede ilk kez kullanmaya çalışırken diğer hesapların kimlik bilgilerini girmeniz istenir.

Bu makalede, birden çok hesabın bu hesaplara nasıl ek Visual Studio. Ayrıca, bağlı hizmet ekle iletişim kutusu, Sunucu Gezgini ve gibi  yerlerde bu hesaplardan  **erişilebilen kaynakları Takım Gezgini.**

## <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

Bir Visual Studio veya Microsoft hesabı hesabıyla oturum açın. Aşağıdakine benzer şekilde, pencerenin üst köşesinde kullanıcı adınız görünür:

![Şu anda oturum açmış kullanıcı](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Azure hesabınıza Sunucu Gezgini

Bu Sunucu Gezgini açmak için Görünüm **Sunucu Gezgini'ı** seçin (veya "Genel" ortam ayarlarını kullanıyorsanız  >   Ctrl Alt S [](../ide/environment-settings.md)  + **tuşlarına** + **basın).** **Azure** düğümünü genişletin ve azure hesabıyla ilişkilendirilmiş Visual Studio azure hesabında bulunan kaynakları içerdiğine dikkat edin. Aşağıdaki görüntüye benzer:

![Sunucu Gezgini Azure düğümü genişletilmiş](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Belirli bir cihazda Visual Studio ilk kez kullanırsanız iletişim kutusu yalnızca oturum açmak için oturum açmak üzere hesabın altında kayıtlı abonelikleri gösterir. **Azure** düğümüne sağ tıklar, Abonelikleri  Yönet ve Filtrele'Sunucu Gezgini ve hesap seçici denetiminden hesaplarınızı ekleyerek diğer hesaplardan herhangi biri için kaynaklara doğrudan erişebilirsiniz. Daha sonra, aşağı oka tıklar ve hesaplar listesinden seçimerek, istenirse başka bir hesap seçebilirsiniz. Hesabı seçtikten sonra, bu hesabın altındaki hangi aboneliklerin **Sunucu Gezgini.**

![Azure Aboneliklerini Yönet iletişim kutusu](../ide/media/vs2015_manage_subs.png)

bir sonraki aç **Sunucu Gezgini** aboneliğin kaynakları görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı Hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişme

1. Mevcut bir projeyi açın veya yeni bir proje oluşturun.

1. içinde proje düğümünü **seçin Çözüm Gezgini** sağ tıklayın ve Bağlı Hizmet **Ekle'yi**  >  **seçin.**

   Bağlı **Hizmet Ekle** sihirbazı görünür ve azure hesabı içinde, azure hesabınızla ilişkilendirilmiş hizmetlerin listesini Visual Studio gösterir. Azure'da ayrı olarak oturum açmanız gerekmez. Ancak, kaynaklarına farklı bir makineden ilk kez erişmeye çalışırken diğer hesaplarda oturum açmanız gerekir.

### <a name="access-azure-active-directory-in-a-web-project"></a>Web Azure Active Directory erişim

Azure Active Directory (AAD), MVC web uygulamaları veya web API ASP.NET AD kimlik doğrulaması için son kullanıcı çoklu oturum açma desteği sağlar. Etki alanı kimlik doğrulaması, bireysel kullanıcı hesabı kimlik doğrulamasından farklıdır. Active Directory etki alanınıza erişimi olan kullanıcılar, web uygulamalarınıza bağlanmak AAD hesaplarını kullanabilir. Microsoft 365 uygulamaları etki alanı kimlik doğrulamasını da kullanabilir.

::: moniker range="vs-2017"

Bunu uygulamalı olarak görmek için Web Uygulaması **ASP.NET Core yeni bir uygulama** oluşturun. Yeni Web **ASP.NET Core iletişim kutusunda** Web Uygulaması şablonunu ve ardından Kimlik Doğrulamasını Değiştir'i **seçin.** 

::: moniker-end

::: moniker range=">=vs-2019"

Bunu uygulamalı olarak görmek için web uygulaması **ASP.NET Core oluşturun.** Yeni bir **web uygulaması ASP.NET Core sayfasında,** **açılan ASP.NET Core 3.1'i** seçin, **Web** Uygulaması şablonunu seçin ve ardından Kimlik Doğrulaması altında **Değiştir'i** **seçin.**

::: moniker-end

Kimlik **Doğrulamasını** Değiştir iletişim kutusu görüntülenir. Burada, uygulamanıza ne tür bir kimlik doğrulaması kullandırabilirsiniz?

![Kimlik doğrulaması iletişim kutusunu ASP.NET](../ide/media/vs2015_change_authentication.png)

'de farklı kimlik doğrulaması türleri hakkında daha fazla bilgi ASP.NET bkz. [ASP.NET'de web projeleri Visual Studio.](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods)

### <a name="access-your-azure-devops-organization"></a>Azure DevOps erişme

Ana menüden Bağlantıları **Yönet'i**  >  **seçen** ekip Takım Gezgini **- Bağlan** açın. Bir **sunucuya**  >  **Bağlan Yönet'i Project.** Bir **Bağlan iletişim Project** listeden bir proje seçin (veya **TFS** Sunucusu Ekle'yi seçin ve sunucunuza yönelik URL'yi girin). Bir URL'yi seçerek kimlik bilgilerinizi yeniden girmenize gerek kalmadan oturum açmış oluruz.

Daha fazla bilgi için [bkz. Bağlan projelerinde Takım Gezgini.](connect-team-project.md)

## <a name="add-an-additional-account-to-visual-studio"></a>Hesaba başka bir hesap Visual Studio

Bu hesaba başka bir hesap eklemek Visual Studio:

1. Dosya   >  **Hesabı'Ayarlar.**

1. Tüm **Hesaplar altında Hesap** **ekle'yi seçin.**

1. Hesapta **oturum açın sayfasında hesabı seçin** veya Başka bir hesap **kullan'ı seçin.** Yeni hesap kimlik bilgilerini girmek için istemleri izleyin.

(İsteğe bağlı) Artık yeni Sunucu Gezgini **hesabıyla** ilişkili Azure hizmetlerini görebilir ve bu hizmetlere gidebilirsiniz. Bu **Sunucu Gezgini** Azure düğümüne sağ tıklayın ve **Abonelikleri** Yönet ve **Filtrele'yi seçin.** Geçerli hesabın yanındaki açılan oka tıklayarak yeni hesabı seçin ve ardından bu hesapta görüntülemek istediğiniz abonelikleri **Sunucu Gezgini.** Belirtilen abonelikle ilişkili tüm hizmetleri görüyor gerekir. Şu anda ikinci hesapla oturum Visual Studio olsa da, o hesabın hizmet ve kaynaklarında oturum açın. Bağlı Hizmet Ekle ve  >  **Project'nin** Bağlan için  >  **de Team Foundation Server.**

### <a name="add-an-account-using-device-code-flow"></a>Cihaz kodu akışını kullanarak hesap ekleme

Bazı durumlarda, düzenli olarak oturum açma veya hesap ekleme gibi durumlar olabilir. Bu durum, Internet Explorer bir nedenle engellenmişse veya ağınız bir güvenlik duvarının arkasında ise olabilir. Bu durumla ilgili bir çalışma yapmak için *cihaz kodu akışını* etkinleştirebilirsiniz. Hesap ekleyebilir veya hesabı yeniden kimlik doğrulamasına sebilirsiniz. Cihaz kodu akışı, farklı bir tarayıcı kullanarak veya fiziksel ya da sanal (VM) farklı bir &mdash; makinede oturum açmanizi sağlar.

Cihaz kodu akışını kullanarak oturum açma:

1. Araçlar Seçenekler [**Ortamı'nın**](reference/accounts-environment-options-dialog-box.md) altındaki **Hesaplar sayfasını** açın ve bir hesap eklerken veya yeniden kimlik doğrularken cihaz kodu akışını  >    >   **etkinleştir'i seçin.** Seçenekler **sayfalarını** kapatmak için Tamam'ı seçin.

1. Hesap **yönetimi**  >  **Ayarlar** açmak için Dosya Hesabı'Ayarlar'yi seçin.

1. Tüm **Hesaplar altında Hesap** **ekle'yi seçin.**

   Bir iletişim kutusu size bir URL ve web tarayıcısına yapıştırmanız gereken kodu gösterir.

   ![Cihaz kod akışı URL'si ve kodu](media/work-with-multiple-user-accounts/device-login-code.png)

1. İletişim kutusunun metnini kopyalamak için **Ctrl** + **C** tuşlarına basın ve ardından **tamam'ı seçarak** iletişim kutusunu kapatın. Kopyalanan metni, kopyalanmış metin düzenleyici gibi bir Not Defteri. Bu, sonraki adımda kodu kopyalamayı kolaylaştırır.

1. Visual Studio'da oturum açasınız ve ardından kopyalayıp Kod olan kutuya yapıştırın veya girmek için kullanmak istediğiniz makinede veya web tarayıcısında cihaz oturum açma URL'sine **gidin.**

   Uygulama **Visual Studio** adı, sayfada daha fazla görünür.

1. Bu Visual Studio Devam'ı **seçin.**

   ![Devam seçeneğini gösteren Cihaz Oturum Açma sayfasının ekran görüntüsü.](media/work-with-multiple-user-accounts/device-login-page.png)

1. Hesap kimlik bilgilerinizi girmek için istemleri izleyin.

   Bir sayfa görüntülenir ve cihazda oturum Visual Studio ve tarayıcı penceresini kapatabilirsiniz.

   ![Visual Studio tarayıcı aracılığıyla oturum açma tamamlandı](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Geri dön sayfasında hesap yönetimi sayfasına Visual Studio yeni eklenen hesabın Tüm Hesaplar altında **listelenmiş olduğunu görebilirsiniz.** **Kapat'ı seçin.**

::: moniker range=">=vs-2019"

### <a name="add-a-github-account-to-visual-studio"></a>Bir GitHub hesabı Visual Studio

Sürüm 16.8'den başlayarak, hem GitHub hem de GitHub Enterprise anahtarlıkları ekabileceksiniz. Microsoft hesaplarıyla olduğu gibi bunları da ekabilecek ve bunlardan yararlanabileceksiniz. Bu sayede farklı hesaplarda GitHub kaynaklarınıza daha kolay Visual Studio.

Ayrıntılı yönergeler için [bkz. GitHub hesaplarıyla Visual Studio.](work-with-github-accounts.md)
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio'da oturum açma](/visualstudio/mac/signing-in)
