---
title: Birden çok kullanıcı hesabıyla çalışma
description: tüm Microsoft hesaplarınızı Visual Studio 'a eklemeyi öğrenin. böylece, kaynaklara ayrı olarak oturum açmanıza gerek kalmadan herhangi bir hesaptan erişebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 44391718babe74dc2c7b2398189909aadec624d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061665"
---
# <a name="work-with-multiple-user-accounts"></a>Birden çok kullanıcı hesabıyla çalışma

birden çok Microsoft hesabınız ve/veya iş veya okul hesabınız varsa, bu kaynakları ayrı olarak oturum açmanıza gerek kalmadan herhangi bir hesaptan erişebilmek için Visual Studio 'e ekleyebilirsiniz. Azure, Application Insights, Azure DevOps ve Microsoft 365 hizmetleri, kolaylaştırılmış oturum açma deneyimini destekler.

bir makineye birden çok hesap ekledikten sonra, başka bir makinede Visual Studio oturum açarsanız, bu hesap kümesi sizinle gezinbir şekilde yapılır.

> [!NOTE]
> Hesap adları dolaşımda olsa da, kimlik bilgileri. Yeni bir makinede kaynaklarını ilk kez kullanmaya çalıştığınızda, bu hesapların kimlik bilgilerini girmeniz istenir.

Bu makalede, Visual Studio için birden çok hesap ekleme konusu gösterilmektedir. Ayrıca, **bağlı hizmet ekle** iletişim kutusu, **Sunucu Gezgini** ve **Takım Gezgini** gibi yerlerde bu hesaplardan erişilebilir kaynakları nasıl göregösterdiğini gösterir.

## <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

bir Microsoft hesabı veya kurumsal hesapla Visual Studio oturum açın. Kullanıcı adınızın pencerenin üst köşesinde göründüğünü, buna benzer şekilde görmeniz gerekir:

![Şu anda oturum açmış Kullanıcı](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Sunucu Gezgini Azure hesabınıza erişin

Sunucu Gezgini açmak için Sunucu Gezgini **görüntüle**' yi seçin  >   (veya "genel" [ortam ayarlarını](../ide/environment-settings.md)kullanıyorsanız **CTRL** + **alt** + **öğeleri**' ne basın. **Azure** düğümünü genişletin ve Visual Studio 'de oturum açmak için kullandığınız hesapla ilişkili Azure hesabında kullanılabilir kaynakları içerdiğine dikkat edin. Aşağıdaki resme benzer şekilde görünür:

![Azure node genişletilmiş Sunucu Gezgini](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

belirli bir cihazda Visual Studio ilk kez kullandığınızda, iletişim kutusu yalnızca ile oturum açtığınız hesap altına kaydedilen abonelikleri gösterir. **Azure** düğümüne sağ tıklayıp **abonelikleri Yönet ve filtrele**' yi seçip hesap Seçicisi denetiminden hesaplarınızı ekleyerek, diğer hesaplarınızdan herhangi birine ait kaynaklara doğrudan **Sunucu Gezgini** erişebilirsiniz. İsterseniz aşağı oka tıklayıp hesaplar listesinden seçerek başka bir hesap seçebilirsiniz. Hesabı seçtikten sonra, bu hesabın altındaki hangi aboneliklerin **Sunucu Gezgini** görüntüleneceğini özelleştirebilirsiniz.

![Azure aboneliklerini yönetme iletişim kutusu](../ide/media/vs2015_manage_subs.png)

**Sunucu Gezgini** bir sonraki açışınızda, bu aboneliğin kaynakları görüntülenir.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Bağlı hizmet Ekle iletişim kutusu aracılığıyla Azure hesabınıza erişin

1. Mevcut bir projeyi açın veya yeni bir proje oluşturun.

1. **Çözüm Gezgini**' de proje düğümünü seçin ve ardından sağ tıklayıp   >  **bağlı hizmet** Ekle ' yi seçin.

   **bağlı hizmet ekleme** sihirbazı görüntülenir ve Visual Studio kişiselleştirme hesabınızla ilişkili Azure hesabındaki hizmetlerin listesini gösterir. Azure 'da ayrı olarak oturum açmanıza gerek yoktur. Ancak, farklı bir makineden kaynaklarına ilk kez erişmeye çalıştığınızda diğer hesaplarda oturum açmanız gerekir.

### <a name="access-azure-active-directory-in-a-web-project"></a>Web projesindeki Azure Active Directory erişim

Azure Active Directory (AAD), web apı hizmetlerindeki ASP.NET MVC web uygulamalarında veya AD kimlik doğrulamasında son kullanıcı çoklu oturum açma desteği sunar. Etki alanı kimlik doğrulaması, bireysel kullanıcı hesabı kimlik doğrulamasından farklıdır. Active Directory etki alanına erişimi olan kullanıcılar, Web uygulamalarınıza bağlanmak için mevcut AAD hesaplarını kullanabilir. Microsoft 365 uygulamalar, etki alanı kimlik doğrulamasını da kullanabilir.

::: moniker range="vs-2017"

bunu eylemde görmek için yeni bir **ASP.NET Core Web uygulaması** projesi oluşturun. **yeni ASP.NET Core web uygulaması** iletişim kutusunda **web uygulaması** şablonunu seçin ve ardından **kimlik doğrulamayı değiştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

bunu eylemde görmek için yeni bir **ASP.NET Core Web uygulaması** projesi oluşturun. **yeni bir ASP.NET Core Web uygulaması oluştur** sayfasında, açılan listeden **ASP.NET Core 3,1** ' i seçin, **Web uygulaması** şablonunu seçin ve ardından **kimlik doğrulaması** altında **değiştir** ' i seçin.

::: moniker-end

Uygulamanızda kullanılacak kimlik doğrulaması türünü seçebileceğiniz **kimlik doğrulamayı Değiştir** iletişim kutusu görüntülenir.

![ASP.NET için kimlik doğrulama iletişim kutusunu Değiştir](../ide/media/vs2015_change_authentication.png)

ASP.NET farklı kimlik doğrulama türleri hakkında daha fazla bilgi için, bkz. [Visual Studio ASP.NET web projeleri oluşturma](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Azure DevOps kuruluşunuza erişin

ana menüden **takım**  >  **bağlantıları yönet** ' i seçerek **Takım Gezgini Bağlan** penceresini açın. Project **Bağlan bağlantıları yönet**' i seçin  >  . **Bağlan bir Project** iletişim kutusunda listeden bir proje seçin (veya **TFS sunucusu ekle** ' yi seçin ve sunucunuza URL 'yi girin). Bir URL seçtiğinizde, kimlik bilgilerinizi yeniden girmeye gerek kalmadan oturum açarsınız.

daha fazla bilgi için bkz. [Takım Gezgini projelere Bağlan](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Visual Studio ek hesap ekleyin

Visual Studio ek bir hesap eklemek için:

1. **dosya**  >  **hesabı Ayarlar** seçin.

1. **Tüm hesaplar** altında **Hesap Ekle**' yi seçin.

1. **Hesabınızda oturum açın** sayfasında hesabı seçin veya **başka bir hesap kullan**' ı seçin. Yeni hesap kimlik bilgilerini girmek için istemleri izleyin.

Seçim Artık **Sunucu Gezgini** giderek, yeni eklediğiniz hesapla ilişkili Azure hizmetlerini görebilirsiniz. **Sunucu Gezgini**' de, **Azure** düğümüne sağ tıklayın ve **abonelikleri Yönet ve filtrele**' yi seçin. Geçerli hesabın yanındaki aşağı açılan oka tıklayarak yeni hesabı seçin ve ardından **Sunucu Gezgini** hangi abonelikleri göstermek istediğinizi seçin. Belirtilen abonelikle ilişkili tüm hizmetleri görmeniz gerekir. şu anda ikinci hesapla Visual Studio oturum açmasanız bile, bu hesabın hizmetleri ve kaynaklarında oturum açtınız. aynı, **Project**  >  **bağlı hizmet** ve **takım**  >  **Bağlan eklemek Team Foundation Server için** de geçerlidir.

### <a name="add-an-account-using-device-code-flow"></a>Cihaz kod akışı kullanarak hesap ekleme

Bazı durumlarda, oturum açamaz ve düzenli olarak bir hesap ekleyemezsiniz. Bu durum Internet Explorer bazı nedenlerle engellenmişse veya ağınız bir güvenlik duvarının arkasındaysa oluşabilir. Bu sorunu geçici olarak çözmek için, *cihaz kodu akışını* bir hesap eklemek veya hesabınızı yeniden kimlik doğrulaması yapmak üzere etkinleştirebilirsiniz. Cihaz kod akışı, farklı bir tarayıcı veya &mdash; fiziksel ya da sanal (VM) ile farklı bir makinede oturum açmanıza olanak tanır.

Cihaz kod akışını kullanarak oturum açmak için:

1. **Araçlar** seçenekler ortamı altında [**hesaplar**](reference/accounts-environment-options-dialog-box.md) sayfasını açın  >    >  ve **bir hesabı eklerken veya yeniden doğrularken cihaz kod akışını etkinleştir**' i seçin. Seçenekler sayfalarını kapatmak için **Tamam ' ı** seçin.

1.   >  hesap yönetimi sayfasını açmak için dosya **hesabı Ayarlar** seçin.

1. **Tüm hesaplar** altında **Hesap Ekle** ' yi seçin.

   Bir iletişim kutusu, bir Web tarayıcısına yapıştıracağınız URL ve kodu gösterir.

   ![Cihaz kod akışı URL 'SI ve kodu](media/work-with-multiple-user-accounts/device-login-code.png)

1.  + İletişim kutusunun metnini kopyalamak için CTRL **C** tuşlarına basın ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı seçin. kopyaladığınız metni Not Defteri gibi bir metin düzenleyicisine yapıştırın. Bu, bir sonraki adımda kodu kopyalamayı kolaylaştırır.

1. Visual Studio 'de oturum açmak için kullanmak istediğiniz makinede veya web tarayıcısında cihaz oturum açma URL 'sine gidin ve ardından **kodu** yazan kutuya kopyaladığınız kodu yapıştırın veya girin.

   **Visual Studio** uygulama adı sayfada daha aşağı görünmelidir.

1. **Visual Studio** altında **devam**' ı seçin.

   ![Devam seçeneğini gösteren cihaz oturum açma sayfasının ekran görüntüsü.](media/work-with-multiple-user-accounts/device-login-page.png)

1. Hesap kimlik bilgilerinizi girmek için istemleri izleyin.

   cihazınızda Visual Studio oturum açmış olduğunu ve tarayıcı penceresini kapatadığınızı bildiren bir sayfa görüntülenir.

   ![Visual Studio tarayıcıda oturum açma tamam](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Visual Studio hesap yönetimi sayfasına geri dönün ve yeni eklenen hesabı **tüm hesaplar** altında listelenmiş olarak görürsünüz. **Kapat**' ı seçin.

::: moniker range=">=vs-2019"

### <a name="add-a-github-account-to-visual-studio"></a>Visual Studio GitHub hesap ekleme

sürüm 16,8 ' den başlayarak anahtarınıza hem GitHub hem de GitHub Enterprise hesabı ekleyebileceksiniz. Microsoft hesapları ile yaptığınız gibi bunları ekleyebilir ve onlardan yararlanabilir. bu, GitHub kaynaklarınıza Visual Studio bir zaman daha kolay erişim sağlayabilmeniz anlamına gelir.

ayrıntılı yönergeler için bkz. [Visual Studio GitHub hesaplarıyla çalışma](work-with-github-accounts.md).
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio oturum açın](/visualstudio/mac/signing-in)
