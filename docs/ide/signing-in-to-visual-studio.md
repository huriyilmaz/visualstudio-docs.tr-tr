---
title: Oturum açın
description: Deneme süresini uzatmak Visual Studio, Visual Studio açma ve daha fazlasını Visual Studio oturum açın
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8d674a46ec68810df8575f963bccf9b2ed70f574
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628533"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Visual Studio'da oturum Windows 

Oturum açmanız gerekmasa da bunun birçok avantajı vardır. Bu makalede oturum açma, [profilinizi](#how-to-sign-in)güncelleştirme ve [](#update-your-profile)bu deneyimin avantajları hakkında bilgi Visual Studio. 

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/signing-in)

::: moniker range="vs-2017"

> [!WARNING]
> Koşullu erişim için yapılandırılmış kaynaklarla çalışmak için, Visual Studio 2019 Güncelleştirme 16.6 veya sonraki bir sürümüne yükseltin. Daha fazla bilgi için [bkz. Çok faktörlü Visual Studio gerektiren hesaplarla yapılandırmayı kullanma.](work-with-multi-factor-authentication.md)
> Koşullu Visual Studio yapılandırılmış kaynaklara erişmek için Visual Studio 2017'yi kullanmak, düzeyi düşürülmüş bir kimlik doğrulama deneyimi tetikler ve aynı oturumda birkaç kez yeniden Visual Studio istenebilir. 
> 
::: moniker-end

Burada, neler bekleyebilirsiniz ve oturum açma sonrasında neler yapabilirsiniz tam listesi ve ardından:

|Avantaj|Description|
|---|---|
|Deneme süresini Visual Studio uzatma|Deneme Visual Studio Professional 30 Visual Studio Enterprise sınırlı olmak yerine **90** gün daha veya daha uzun bir süre boyunca kullanın. <br/>Bkz. [Deneme sürümünü genişletme veya lisansı güncelleştirme.](../ide/how-to-unlock-visual-studio.md)|
|Visual Studio kilidini açma (Visual Studio aboneliği veya Azure DevOps kuruluş)|Visual Studio aboneliği veya Visual Studio kuruluş ile ilişkili bir hesap kullanıyorsanız Azure DevOps açın.<br/>Bkz. [Deneme sürümünü genişletme veya lisansı güncelleştirme.](../ide/how-to-unlock-visual-studio.md)|
|Uygulama ayarlarınızı Visual Studio eşitleme|Ayarlar bağlamalar, pencere düzeni ve renk teması gibi özelleştirebileceğiniz her şey, herhangi bir cihazda oturum Visual Studio hemen uygulanır. <br/>Bkz. [Eşitleme ayarları Visual Studio.](../ide/synchronized-settings-in-visual-studio.md)|
|Hizmetlere otomatik olarak bağlanma|Bağlan kimlik bilgilerini yeniden girmenize gerek kalmadan IDE'de Azure ve Azure DevOps Services gibi hizmetlere erişebilirsiniz.|
|Visual Studio Community sürümünü kullanmaya devam|Community sürümünüz yüklemesi sizden bir lisans istenirse, ücretsiz olarak Visual Studio Community devam etmek için IDE'de oturum **açın.** |
|'Visual Studio Dev Essentials' al|Bu program ücretsiz yazılım teklifleri, eğitim, destek ve daha fazlasını içerir. <br/>Bkz. [Visual Studio Dev Essentials.](https://visualstudio.microsoft.com/dev-essentials/)|


## <a name="how-to-sign-in"></a>Oturum açma 

Oturum Visual Studio için oturum açıp bazı temel kayıt bilgilerini sağlamanız istenmektedir.

![Oturum açma istemi](../ide/media/vs2019_signinpopup.png)

1. Bir Microsoft hesabı veya sizi en iyi temsil eden iş veya okul hesabını seçin. Bu hesaplardan herhangi biri yoksa, oturum açma Microsoft hesabı tıklayarak ücretsiz bir hesap oluşturabilirsiniz. Sorun varsa bkz. Nasıl yaparım? [kaydolma Microsoft hesabı?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Kullanıcı arabiriminde kullanmak istediğiniz kullanıcı arabirimi ayarlarını ve renk temasını Visual Studio. Visual Studio bu ayarları anımsar ve oturum Visual Studio tüm ortamlar arasında eşitler. Eşitlenen ayarların listesi için bkz. [Eşitlenmiş ayarlar.](../ide/synchronized-settings-in-visual-studio.md) Daha sonra araçlar menüsünde Araçlar Seçenekler menüsünü **açarsanız**  >  **ayarları değiştirebilirsiniz** Visual Studio.
   Ayarları yaptıktan sonra Visual Studio başlatılır, oturumunuz açılır ve başlamaya hazır olursunuz. 
   
1. Oturum a kimliğinizi doğrulamak için ortamın sağ üst köşesinde adınıza Visual Studio.

![ŞU anda VS2019'da oturum açmış kullanıcı](../ide/media/vs2019_username.png)

Oturum açmayı tercih Visual Studio daha sonra kolayca açabilirsiniz. Oturum açma **ortamının** sağ üst köşesindeki Oturum Visual Studio bakın.

![Oturum alanı kullanıcı](../ide/media/vs2019_usernotsignedin.png)

Oturum açmadıysanız, oturum her Visual Studio otomatik olarak oturum açılır ve eşitlenen ayarlarda yapılan tüm değişiklikler otomatik olarak uygulanır. Oturum açma için, Visual Studio ortamının sağ üst köşesindeki profil adınızla simgeye tıklayın, Hesap ayarları komutunu seçin ve ardından **Oturumdan çık bağlantısını** seçin.  Yeniden oturum açma için **ortamının** sağ üst köşesindeki Oturum Visual Studio seçin.

## <a name="update-your-profile"></a>Profilinizi güncelleştirme

1. Dosya Hesabı  >   Ayarlar'a gidin ve **Visual Studio profilini yönet bağlantısını** seçin.

1. Tarayıcı penceresinde Profili **düzenle'yi** seçin ve istediğiniz ayarları değiştirin.

1. Bitirin, Değişiklikleri **kaydet'i seçin.**

## <a name="troubleshooting"></a>Sorun giderme

Yardım almak [için Abonelik](https://visualstudio.microsoft.com/subscriptions/support/) destek sayfasına bakın.
