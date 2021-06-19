---
title: Windows'da oturum açma
description: Oturum açma hakkında bilgi Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b0ed679188cc0a4df9329fdd0adff4ad69667e6
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375766"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Windows'da Visual Studio oturum açma

Oturum açmanız gerekmasa da bunun birçok avantajı vardır. Oturum aken, kullanıcı deneyiminizi kişiselleştirerek, iyileştirerek ve zenginleştirerek Visual Studio edin. 

> [!NOTE]
> Bu konu Windows'Visual Studio için geçerlidir. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/signing-in)

::: moniker range="vs-2017"

> [!WARNING]
> Koşullu erişim için yapılandırılmış kaynaklarla çalışmak için, Visual Studio 2019 Güncelleştirme 16.6 veya sonraki bir sürümüne yükseltin. Daha fazla bilgi için [bkz. Çok faktörlü Visual Studio gerektiren hesaplarla yapılandırmayı kullanma.](work-with-multi-factor-authentication.md)
> Koşullu Visual Studio yapılandırılmış kaynaklara erişmek için Visual Studio 2017'yi kullanmak, düzeyi düşürülmüş bir kimlik doğrulama deneyimi tetikler ve aynı oturumda birkaç kez yeniden kimlik doğrulaması Visual Studio tetikler. 
> 
::: moniker-end

## <a name="benefits"></a>Avantajlar

Burada, neler bekleyebilirsiniz ve oturum açma sonrasında neler yapabilirsiniz tam listesi ve ardından:


#### <a name="extend-the-visual-studio-trial-period"></a>Deneme süresini Visual Studio uzatma

30 günlük Visual Studio Professional Visual Studio Enterprise süreyle sınırlı olmak yerine, 90 gün boyunca bir veya daha fazla süre boyunca Visual Studio Professional veya daha uzun bir süre kullanabilirsiniz. Daha fazla bilgi için [bkz. Deneme sürümünü genişletme veya lisansı güncelleştirme.](../ide/how-to-unlock-visual-studio.md)

#### <a name="synchronize-your-visual-studio-settings"></a>Uygulama ayarlarınızı Visual Studio eşitleme

Anahtar bağlamaları, pencere düzeni ve renk teması gibi özelleştirebileceğiniz ayarlar, herhangi bir cihazda oturum Visual Studio hemen uygulanır. Bkz. [Eşitleme ayarları Visual Studio.](../ide/synchronized-settings-in-visual-studio.md)

#### <a name="use-visual-studio-community-edition"></a>Visual Studio Community sürümünü kullanma

Community sürümü yüklemesi sizden lisans istenirse, ücretsiz olarak bir lisans kullanarak devam etmek Visual Studio Community IDE'de oturum **açın.** 

#### <a name="unlock-visual-studio-visual-studio-subscription-or-an-azure-devops-organization"></a>Visual Studio (Visual Studio veya Azure DevOps kuruluş) kilidini açma

Deneme Visual Studio uzatma veya bir lisansı güncelleştirme adımlarını kullanarak Visual Studio aboneliği veya Azure DevOps kuruluş ile ilişkili bir hesap kullanıyorsanız, bu hesabın [kilidini açın.](../ide/how-to-unlock-visual-studio.md)

#### <a name="the-visual-studio-dev-essentials-program"></a>Visual Studio Dev Essentials programı

Bu program ücretsiz yazılım teklifleri, eğitim, destek ve daha fazlasını içerir. Daha [fazla Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) için bkz. Visual Studio Dev Essentials.

#### <a name="automatically-connect-to-services"></a>Hizmetlere otomatik olarak bağlanma

Aynı hesabın kimlik bilgilerini yeniden Azure DevOps Services olmadan IDE'de Azure ve Azure DevOps Services gibi hizmetlere bağlanın.

## <a name="how-to-sign-in"></a>Oturum açma 

İlk Visual Studio için oturum açıp bazı temel kayıt bilgilerini sağlamanız istenmektedir.

![Oturum açma istemi](../ide/media/vs2019_signinpopup.png)

1. Bir Microsoft hesabı veya sizi en iyi temsil eden iş veya okul hesabını seçin. Bu hesaplardan herhangi biri yoksa, oturum açma düğmesinin altındaki bağlantıya tıklayarak Microsoft hesabı ücretsiz bir hesap oluşturabilirsiniz. Sorun varsa bkz. Nasıl yaparım? [kaydolma Microsoft hesabı?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Kullanıcı arabiriminde kullanmak istediğiniz kullanıcı arabirimi ayarlarını ve renk temasını Visual Studio. Visual Studio bu ayarları anımsar ve oturum Visual Studio tüm ortamlar arasında eşitler. Eşitlenen ayarların listesi için bkz. [Eşitlenmiş ayarlar.](../ide/synchronized-settings-in-visual-studio.md) Daha sonra araçlar menüsünde Araçlar Seçenekler menüsünü **açarsanız**  >  **ayarları** değiştirebilirsiniz Visual Studio.
   Ayarları yaptıktan sonra Visual Studio başlatılır, oturumunuz açılır ve başlamaya hazır olursunuz. 
   
1. Oturum a kimliğinizi doğrulamak için ortamın sağ üst köşesinde adınıza Visual Studio.

![ŞU anda VS2019'da oturum açmış kullanıcı](../ide/media/vs2019_username.png)

Oturum açmayı tercih Visual Studio daha sonra kolayca açabilirsiniz. Oturum açma **ortamının** sağ üst köşesindeki Oturum Visual Studio bakın.

![Oturum alanı kullanıcı](../ide/media/vs2019_usernotsignedin.png)

Oturum açmadıysanız, oturum her Visual Studio otomatik olarak oturum açılır ve eşitlenen ayarlarda yapılan tüm değişiklikler otomatik olarak uygulanır. Oturum açma için, Visual Studio ortamının sağ üst köşesindeki profil adınızla simgeye tıklayın, Hesap ayarları komutunu seçin ve ardından **Oturumdan çık bağlantısını** seçin.  Yeniden oturum açma için ortam **ortamının** sağ üst köşesindeki Oturum Visual Studio seçin.

## <a name="update-your-profile"></a>Profilinizi güncelleştirme

1. Dosya Hesabı  >  **Ayarları'ne gidin** ve Yönetim **profili Visual Studio seçin.**

1. Tarayıcı penceresinde Profili **düzenle'yi** seçin ve istediğiniz ayarları değiştirin.

1. Bitirin, Değişiklikleri **kaydet'i seçin.**

## <a name="troubleshooting"></a>Sorun giderme

Yardım almak [için Abonelik](https://visualstudio.microsoft.com/subscriptions/support/) destek sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Deneme sürümü uzatma veya bir lisansı güncelleştirme](../ide/how-to-unlock-visual-studio.md)
* [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
* [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
