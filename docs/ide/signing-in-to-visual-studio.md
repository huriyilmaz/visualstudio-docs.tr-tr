---
title: Oturum açın
description: Visual Studio deneme süresini uzatmak için Visual Studio oturum açın, Visual Studio kilidini açın ve daha fazlasını yapın
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b4c91a2ff4693b62ce8ac4d40d493995c52b81b
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549478"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Windows Visual Studio için oturum açın 

Oturum açmanız gerekmiyorsa, bunu yapmanın pek çok avantajı vardır. bu makalede, [oturum açma](#how-to-sign-in), [profilinizi güncelleştirme](#update-your-profile)ve Visual Studio deneyiminizin avantajları hakkında bilgi edineceksiniz. 

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio oturum açma](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> koşullu erişim için yapılandırılmış kaynaklarla çalışmak için Visual Studio 2019 güncelleştirme 16,6 veya sonraki bir sürüme yükseltin. daha fazla bilgi için bkz. [multi-factor authentication gerektiren hesaplarla Visual Studio kullanma](work-with-multi-factor-authentication.md).
> koşullu erişim için yapılandırılmış kaynaklara erişmek üzere Visual Studio 2017 kullanmak, azaltılmış bir kimlik doğrulama deneyimi tetikleyip aynı Visual Studio oturumunda birkaç kez yeniden kimlik doğrulaması işlemi tetiklenebilir. 
> 
::: moniker-end

İşte, oturum açtıktan sonra neleri beklediklerinize ilişkin tam bir liste aşağıda verilmiştir:

|Avantaj|Description|
|---|---|
|Visual Studio deneme süresini uzat|30 günlük deneme süresi ile sınırlı olmak yerine, **ek 90 gün boyunca** Visual Studio Professional veya Visual Studio Enterprise kullanın. <br/>Bkz. [deneme sürümünü genişletme veya lisans güncelleştirme](../ide/how-to-unlock-visual-studio.md).|
|Visual Studio kilit açma (Visual Studio abonelik veya Azure DevOps kuruluş)|Visual Studio aboneliği veya Azure DevOps organizasyonu ile ilişkili bir hesap kullanıyorsanız, Visual Studio açın.<br/>Bkz. [deneme sürümünü genişletme veya lisans güncelleştirme](../ide/how-to-unlock-visual-studio.md).|
|Visual Studio ayarlarınızı eşitler|anahtar bağlamaları, pencere düzeni ve renk teması gibi özelleştirdiğiniz Ayarlar, herhangi bir cihazda Visual Studio oturum açtığınızda hemen uygulanır. <br/>Bkz. [Visual Studio ayarları senkronize](../ide/synchronized-settings-in-visual-studio.md)etme.|
|Hizmetlere otomatik olarak bağlan|aynı hesapta kimlik bilgileri için yeniden sormadan, Azure ve Azure DevOps Services gibi hizmetlere Bağlan.|
|Visual Studio Community sürümünü kullanmaya devam et|Community edition yüklemeniz bir lisans isterse, Visual Studio Community **ücretsiz** kullanmaya devam etmek için ıde 'de oturum açın. |
|' Visual Studio Dev Essentials ' al|Bu program ücretsiz yazılım teklifleri, eğitim, destek ve daha fazlasını içerir. <br/>bkz. [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Oturum açma 

Visual Studio ilk kez açtığınızda, oturum açmanız ve bazı temel kayıt bilgilerini sağlamanız istenir.

![Oturum açma istemi](../ide/media/vs2019_signinpopup.png)

1. Sizi en iyi şekilde temsil eden bir Microsoft hesabı veya bir iş veya okul hesabı seçin. Bu hesaplardan herhangi birine sahip değilseniz, oturum aç düğmesinin altındaki bağlantıya tıklayarak bir Microsoft hesabı ücretsiz olarak oluşturabilirsiniz. Sorun yaşıyorsanız, [Microsoft hesabı nasıl yaparım? kaydolma](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create) bölümüne bakın.

2. Visual Studio içinde kullanmak istediğiniz kullanıcı arabirimi ayarlarını ve renk temasını seçin. Visual Studio bu ayarları anımsar ve oturum açmış olduğunuz tüm Visual Studio ortamlarında eşitlenir. Eşitlenen ayarların listesi için bkz. [Eşitlenmiş Ayarlar](../ide/synchronized-settings-in-visual-studio.md).   >  Visual Studio ' de araçlar **seçenekler** menüsünü açarsanız ayarları daha sonra değiştirebilirsiniz.
   Ayarları yaptıktan sonra Visual Studio başlatılır, oturumunuz açılır ve başlamaya hazır olursunuz. 
   
1. oturum açmış olup olmadığını doğrulamak için Visual Studio ortamının sağ üst köşesinde adınızı arayın.

![VS2019 'de Şu anda oturum açmış olan Kullanıcı](../ide/media/vs2019_username.png)

Visual Studio ilk kez açtığınızda oturum açmayı tercih ediyorsanız daha sonra kolayca yapabilirsiniz. Visual Studio ortamının sağ üst köşesindeki **oturum aç** bağlantısına bakın.

![Oturum açmamış Kullanıcı](../ide/media/vs2019_usernotsignedin.png)

oturumu kapatmadığınız takdirde, her başlattığınızda Visual Studio otomatik olarak oturum açtınız ve eşitlenmiş ayarlarda yapılan değişiklikler otomatik olarak uygulanır. oturumu kapatmak için, Visual Studio ortamının sağ üst köşesindeki profil adınızla simgeye tıklayın, **hesap ayarları** komutunu seçin ve ardından **oturumu kapat** bağlantısını seçin. yeniden oturum açmak için Visual Studio ortamının sağ üst köşesindeki **oturum aç** komutunu seçin.

## <a name="update-your-profile"></a>Profilinizi güncelleştirme

1. Ayarlar **dosya**  >  **hesabı** ' na gidin ve **Visual Studio profilini yönet** bağlantısını seçin.

1. Tarayıcı penceresinde **Profili Düzenle** ' yi seçin ve istediğiniz ayarları değiştirin.

1. İşiniz bittiğinde **Değişiklikleri Kaydet**' i seçin.

## <a name="troubleshooting"></a>Sorun giderme

Yardım almak için [abonelik desteği](https://visualstudio.microsoft.com/subscriptions/support/) sayfasına bakın.
