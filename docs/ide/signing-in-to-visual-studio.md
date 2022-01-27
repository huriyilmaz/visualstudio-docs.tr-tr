---
title: Oturum açın
description: Visual Studio deneme süresini uzatmak için Visual Studio oturum açın, Visual Studio kilidini açın ve daha fazlasını yapın
ms.custom: contperf-fy21q1
ms.date: 12/10/2021
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2c5198d2b99f2f808e3c42c2f35bfcfd9188941a
ms.sourcegitcommit: ebd651e00fe3bae5914c211c4828219bf7d1fc70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137798606"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Windows Visual Studio için oturum açın 

Bu makalede şunları öğreneceksiniz:
+ [Hesap oturum açma avantajları](#benefits)
+ Bir hesapla [oturum açma](#sign-in)
+ [Profilinizi güncelleştirme](#update-your-profile)

::: moniker range="vs-2017"

> [!WARNING]
> koşullu erişim veya multi-factor authentication için yapılandırılmış kaynaklarla çalışmak için Visual Studio 2019 güncelleştirme 16,6 veya üzeri bir sürüm gerekir. daha önceki sürümler, azaltılmış bir kimlik doğrulama deneyimi tetikleyip aynı Visual Studio oturumunda birkaç kez yeniden kimlik doğrulamaya neden olabilir. 

::: moniker-end

<a name="benefits"></a>
## <a name="benefits-why-sign-in"></a>Avantajlar: neden oturum açma? 

Oturum açmanız gerekmiyorsa, bunu yapmanın pek çok avantajı vardır.   

|Avantaj|Description|
|---|---|
|[Visual Studio deneme süresini genişletin](../ide/how-to-unlock-visual-studio.md)|30 günlük deneme süresi ile sınırlı olmak yerine, **ek 90 gün boyunca** Visual Studio Professional veya Visual Studio Enterprise kullanın.|
|[Visual Studio kilidini aç](../ide/how-to-unlock-visual-studio.md)|[Visual Studio aboneliği](/visualstudio/subscriptions/using-the-subscriber-portal) veya Azure DevOps organizasyonu ile ilişkili bir hesap kullanıyorsanız, Visual Studio açın.|
|Ayarlarınızı [eşitler](../ide/synchronized-settings-in-visual-studio.md)|anahtar bağlamaları, pencere düzeni ve renk teması gibi özelleştirdiğiniz Ayarlar, herhangi bir cihazda Visual Studio oturum açtığınızda hemen uygulanır.|
|Azure hizmetlerine otomatik bağlanma|aynı hesapta kimlik bilgileri için yeniden sormadan, Azure ve Azure DevOps Services gibi hizmetlere Bağlan.|
|Community sürümünüzü kullanmaya devam edin|yükleme sizden bir lisans isterse, Visual Studio Community **ücretsiz** kullanmaya devam etmek için ıde 'de oturum açın. |
|[' Visual Studio Dev Essentials ' al](https://visualstudio.microsoft.com/dev-essentials/)|Bu program ücretsiz yazılım, eğitim, destek ve daha fazlasını içerir.|

<a name="sign-in"></a>
## <a name="sign-in-to-account"></a>Hesap oturumu açma

::: moniker range="<=vs-2019"

1. Visual Studio başlatın. Visual Studio ilk kez açtığınızda, oturum açmanız ve bazı temel kayıt bilgilerini sağlamanız istenir.

   ![Oturum açma istemi](../ide/media/vs2019_signinpopup.png)
   
   > [!NOTE]
   > Visual Studio ilk kez açtığınızda oturum açmayı tercih ediyorsanız daha sonra kolayca yapabilirsiniz. Visual Studio ortamının sağ üst köşesindeki **oturum aç** bağlantısına bakın.

::: moniker-end

::: moniker range="vs-2022"

1. Visual Studio başlatın.  Visual Studio ilk kez açtığınızda, oturum açmanız ve bazı temel kayıt bilgilerini sağlamanız istenir.

   ![Oturum açma istemi](../ide/media/vs-2022/visual-studio-sign-in-pop-up.png)

::: moniker-end

2. Microsoft hesabı veya bir iş veya okul hesabı seçin.  Bir tane yoksa, **oturum aç** düğmesinin yakınında bulunan bağlantıyı seçerek [ücretsiz olarak bir Microsoft hesabı oluşturun](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create) . 

3. Tercih ettiğiniz renk temasını ve diğer kullanıcı arabirimi ayarlarını seçin.  Visual Studio [bu ayarları anımsar ve](../ide/synchronized-settings-in-visual-studio.md) oturum açmış olduğunuz tüm Visual Studio ortamlarında eşitlenir.   >  Visual Studio ' de araçlar **seçenekler** menüsünü açarsanız ayarları daha sonra değiştirebilirsiniz.

   Visual Studio ortamının sağ üst köşesinde başarıyla oturum açtığınızdan emin olabilirsiniz.   oturumu kapatmadığınız takdirde, her başlattığınızda Visual Studio otomatik olarak oturum açtınız ve eşitlenmiş ayarlarda yapılan değişiklikler otomatik olarak uygulanır.

::: moniker range="<=vs-2019"

   ![VS2019 'de Şu anda oturum açmış olan Kullanıcı](../ide/media/vs2019_username.png)

::: moniker-end

::: moniker range="vs-2022"

   ![VS2019 'de Şu anda oturum açmış olan Kullanıcı](../ide/media/vs-2022/visual-studio-sign-in.png)

::: moniker-end


## <a name="sign-out-of-account"></a>Hesap oturumunuzu kapat

1. Visual Studio ortamının sağ üst köşesindeki profil adınızla simgeye tıklayın
2. **Hesap ayarları** komutunu seçin.
3. **Oturumu** kapat bağlantısını seçin. 

## <a name="update-your-profile"></a>Profilinizi güncelleştirme

1. Ayarlar **dosya**  >  **hesabı** ' na gidin ve **Visual Studio profilini yönet** bağlantısını seçin.
1. Tarayıcı penceresinde **Profili Düzenle** ' yi seçin ve istediğiniz ayarları değiştirin.
1. İşiniz bittiğinde **Değişiklikleri Kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- Sorun giderme: [abonelik desteği](https://visualstudio.microsoft.com/subscriptions/support/)
- [Visual Studio 2022 sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/)
