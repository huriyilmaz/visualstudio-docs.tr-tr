---
title: Visual Studio’da oturum açma
description: Visual Studio 'da oturum açmayı öğrenin.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bc45ae5732db5033a1b123ef18cda27c426fd6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878532"
---
# <a name="sign-in-to-visual-studio"></a>Visual Studio’da oturum açma

Kişiselleştirme hesabınızda oturum açarak, Visual Studio 'da geliştirme deneyiminizi kişiselleştirebilir ve iyileştirebilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio oturum açma](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! Uyarı] koşullu erişim için yapılandırılmış kaynaklara erişmek için Visual Studio 2017 kullanılması, azaltılmış bir kimlik doğrulama deneyimi tetikleyip aynı Visual Studio oturumunda birkaç kez yeniden kimlik doğrulaması istenebilir. 
> Koşullu erişim için yapılandırılmış kaynaklarla çalışmak için Visual Studio 2019 güncelleştirme 16,6 veya sonraki bir sürüme yükseltin. Daha fazla bilgi için bkz. [Multi-Factor Authentication gerektiren hesaplarla Visual Studio 'yu kullanma](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Neden Visual Studio'da oturum açmam gerekiyor?

Oturum açtığınızda, Visual Studio deneyiminizi zenginleştirin. Örneğin, oturum açtıktan sonra, ayarlarınızı cihaz genelinde [eşitleyebilir](synchronized-settings-in-visual-studio.md) , bir denemeyi genişletebilir ve bir Azure hizmetine otomatik olarak bağlanarak birkaç tane adı verebilirsiniz.

İşte, oturum açtıktan sonra neleri beklediklerinize ilişkin tam bir liste aşağıda verilmiştir:
- **Visual Studio deneme süresini genişletin** -30 günlük deneme süresi boyunca sınırlı olmak yerine Visual Studio Professional veya Visual Studio Enterprise ek 90 gün boyunca kullanabilirsiniz. Daha fazla bilgi için bkz. [deneme sürümünü genişletme veya lisans güncelleştirme](../ide/how-to-unlock-visual-studio.md).

- **Visual Studio Community Edition 'ı kullanmaya devam et** -topluluk sürümü yüklemeniz bir lisans ısterse, Visual Studio Community 'yi **ücretsiz** kullanmaya devam etmek için IDE 'de oturum açın. 

- **Visual Studio aboneliği veya bir Azure DevOps organizasyonu ile ilişkili bir hesap kullanıyorsanız, Visual Studio 'Nun kilidini açın**. Ayrıntılı yönergeler için bkz. [deneme sürümünü genişletme veya lisans güncelleştirme](../ide/how-to-unlock-visual-studio.md).

- **Visual Studio Dev Essentials programına erişim** -bu program ücretsiz yazılım teklifleri, eğitim, destek ve daha fazlasını içerir. Daha fazla bilgi için bkz. [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Visual Studio ayarlarınızı eşitler** -anahtar bağlamaları, pencere düzeni ve renk teması gibi özelleştirdiğiniz ayarlar, Visual Studio 'da herhangi bir cihazda oturum açtığınızda hemen uygulanır. Bkz. [Visual Studio 'da ayarları eşitler](../ide/synchronized-settings-in-visual-studio.md).

- Aynı hesapta kimlik bilgileri için yeniden sormadan **Azure ve Azure DevOps Services gibi hizmetlere otomatik olarak bağlanın** .

## <a name="how-to-sign-in-to-visual-studio"></a>Visual Studio 'da oturum açma

Visual Studio 'Yu ilk kez açtığınızda, oturum açmanız ve bazı temel kayıt bilgilerini sağlamanız istenir.

![Oturum açma istemi](../ide/media/vs2019_signinpopup.png)

Sizi en iyi şekilde temsil eden bir Microsoft hesabı veya bir iş veya okul hesabı seçmelisiniz. Bu hesaplardan herhangi birine sahip değilseniz, oturum aç düğmesinin altındaki bağlantıya tıklayarak bir Microsoft hesabı ücretsiz olarak oluşturabilirsiniz. Sorun yaşıyorsanız, [Microsoft hesabı nasıl yaparım? kaydolma](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create) bölümüne bakın.

Daha sonra, Visual Studio'da kullanmak istediğiniz kullanıcı arabirimi ayarlarını ve renk temasını seçin. Visual Studio bu ayarları anımsar ve oturum açtığınız tüm Visual Studio ortamlarında eşitlenir. Eşitlenen ayarların listesi için bkz. [Eşitlenmiş Ayarlar](../ide/synchronized-settings-in-visual-studio.md).   >  Visual Studio 'da Araçlar **Seçenekler** menüsünü açarsanız ayarları daha sonra değiştirebilirsiniz.

Ayarları yaptıktan sonra Visual Studio başlatılır, oturumunuz açılır ve başlamaya hazır olursunuz. Oturum açmış olup olmadığını doğrulamak için, Visual Studio ortamının sağ üst köşesinde adınızı arayın.

![VS2019 'de Şu anda oturum açmış olan Kullanıcı](../ide/media/vs2019_username.png)

Visual Studio 'Yu ilk kez açtığınızda oturum açmayı tercih ediyorsanız daha sonra kolayca yapabilirsiniz. Visual Studio ortamının sağ üst köşesindeki **oturum aç** bağlantısına bakın.

![Oturum açmamış Kullanıcı](../ide/media/vs2019_usernotsignedin.png)

Oturumu kapatmadığınız takdirde, Visual Studio 'Yu her başlattığınızda otomatik olarak oturum açtınız ve eşitlenmiş ayarlarda yapılan değişiklikler otomatik olarak uygulanır. Oturumu kapatmak için, Visual Studio ortamının sağ üst köşesindeki profil adınızla simgeye tıklayın, **Hesap ayarları** komutunu seçin ve ardından **Oturumu Kapat** bağlantısını seçin. Yeniden oturum açmak için Visual Studio ortamının sağ üst köşesindeki **oturum aç** komutunu seçin.

## <a name="to-change-your-profile-information"></a>Profil bilginizi değiştirmek için

1. **Dosya**  >  **hesabı ayarları** ' na gidin ve **Visual Studio profilini Yönet** bağlantısını seçin.

1. Tarayıcı penceresinde **Profili Düzenle** ' yi seçin ve istediğiniz ayarları değiştirin.

1. İşiniz bittiğinde **Değişiklikleri Kaydet**' i seçin.

## <a name="troubleshooting"></a>Sorun giderme

Oturum açarken herhangi bir sorunla karşılaşırsanız, yardım almak için lütfen [abonelik desteği](https://visualstudio.microsoft.com/subscriptions/support/) sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Deneme sürümü uzatma veya bir lisansı güncelleştirme](../ide/how-to-unlock-visual-studio.md)
* [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
* [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
* [Oturum aç (Mac için Visual Studio)](/visualstudio/mac/signing-in)
* [Etkinleştirme (Mac için Visual Studio)](/visualstudio/mac/activation)
