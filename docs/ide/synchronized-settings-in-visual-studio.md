---
title: Ayarları eşitler
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566793"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Visual Studio ayarlarını birden çok bilgisayar arasında eşitler

Aynı kişiselleştirme hesabını kullanarak Visual Studio 'da birden çok bilgisayarda oturum açtığınızda, ayarlarınız bilgisayarlar arasında eşitlenebilir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar

Varsayılan olarak, aşağıdaki ayarlar eşitlenir:

- Geliştirme ayarları. Visual Studio 'Yu ilk kez açtığınızda bir ayarlar koleksiyonu seçersiniz, ancak seçimi dilediğiniz zaman değiştirebilirsiniz. Daha fazla bilgi için [ortam ayarları](../ide/environment-settings.md).

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarının nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

- Pencere **düzenleri sayfasını yönet** > **pencerede** Kullanıcı tanımlı pencere düzenleri.

- **Araçlar** > **seçenekleri** sayfalarındaki aşağıdaki seçenekler:

  - **Ortam** > **genel** seçenekler sayfasındaki Tema ve menü çubuğu büyük/küçük harf ayarları.

  - **Ortamdaki** tüm ayarlar **yazı tipleri ve renkler** Seçenekler sayfası > .

  - **Ortam** > **klavye** seçenekleri sayfasındaki tüm klavye kısayolları.

  - **Ortamdaki** tüm ayarlar > **Sekmeler ve Windows** seçenekleri sayfası.

  - **Ortam** > **başlatma** seçenekleri sayfasındaki tüm ayarlar.

  - **Metin düzenleyici** seçenekleri sayfalarındaki tüm ayarlar (örneğin, [kod stili tercihleri](code-styles-and-code-cleanup.md)).

  - **XAML Tasarımcısı** seçenekleri sayfalarındaki tüm ayarlar.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Belirli bir bilgisayardaki eşitlenmiş ayarları kapat

Eşitlenmiş ayarlar Visual Studio için varsayılan olarak açık olabilir. Bir bilgisayardaki eşitlenmiş ayarları, **araçlar** > **seçenekler** > **ortam** > **hesapları** sayfasına giderek ve **Visual Studio 'da oturum açıldığında cihazların içindeki ayarları eşitlemeyi**kaldırarak devre dışı bırakabilirsiniz.

Örnek olarak, "A" bilgisayarında Visual Studio 'nun ayarlarını eşitlememeye karar verirseniz, "A" bilgisayarında yapılan herhangi bir ayar değişikliği "B" bilgisayarında veya "C" bilgisayarında görünmez. "B" ve "C" bilgisayarları birbirleriyle eşitlemeye devam eder, ancak "A" bilgisayarıyla kalmaz.

> [!NOTE]
> **Araçlar** > **seçenekler** > **ortam** > **hesapları** sayfasındaki seçeneği kaldırarak ayarları eşitlememeniz tercih ediyorsanız, Visual Studio 'nun aynı bilgisayardaki diğer sürümleri veya sürümleri bundan etkilenmez. Visual Studio 'nun bu yan yana yüklemeleri, ayarlarını eşitlemeye devam edecektir (çok fazla onay işareti yoksa).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ailesi ürünleri ve sürümleri üzerinde ayarları eşitler

Ayarlar, Visual Studio 'nun sürümleri *ve yan yana yüklenmiş olarak*eşitlenir. Ayrıca, Visual Studio için Blend dahil olmak üzere Visual Studio ailesi ürünleri arasında da eşitlenir. Ancak, tek bir aile ürününün Visual Studio ile paylaşılmayan kendi ayarları olabilir. Örneğin, "A" bilgisayarındaki Visual Studio için Blend özgü ayarlar, "A" veya "B" bilgisayarlarında Visual Studio ile paylaşılmaz.

## <a name="side-by-side-synchronized-settings"></a>Yan yana eşitlenmiş ayarlar

::: moniker range="vs-2017"

Araç penceresi düzeni gibi bazı ayarlar, Visual Studio 'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%Userprofile%\Visual Studio 2017 \ Settings* Içindeki *Currentsettings. vssettings* dosyası, *%LocalAppData%\microsoft\visualstudio\15.0_xxxxxxxx \settings*ile benzer bir yüklemeye özgü klasörde yer alır.

> [!NOTE]
> Yüklemeye özgü yeni ayarları kullanmak için yeni bir yükleme yapın. Var olan bir Visual Studio yüklemesini yükselttiğinizde, mevcut paylaşılan konum kullanılır.

Şu anda Visual Studio 'nun yan yana yüklemelerine sahipseniz ve yüklemeye özgü yeni ayarlar dosya konumunu kullanmak istiyorsanız, aşağıdaki adımları izleyin:

1. Visual Studio 2017 sürüm 15,3 veya sonraki bir sürüme yükseltin.

2. Tüm mevcut ayarlarınızı, *%LocalAppData%\microsoft\visualstudio\15.0_xxxxxxxx* klasörü dışında bir konuma aktarmak için **Içeri ve dışarı aktarma ayarlarını** kullanın.

3. **VS 2017 için geliştirici komut istemi** açın ve `devenv /resetuserdata`çalıştırın.

1. Visual Studio 'Yu açın ve dışarı aktarılan ayarlar dosyasından kaydedilen ayarları içeri aktarın.

::: moniker-end

::: moniker range=">=vs-2019"

Araç penceresi düzeni gibi bazı ayarlar, Visual Studio 'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%Userprofile%\Visual Studio 2019 \ Settings* Içindeki *Currentsettings. vssettings* dosyası, *%LocalAppData%\microsoft\visualstudio\16.0_xxxxxxxx \settings*ile benzer bir yüklemeye özgü klasördür.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Eşitlenmiş ayarları Sıfırla

Tüm ayarları varsayılan değerlerine sıfırlamak için, Visual Studio 'da oturum açın ve ardından ayarları içeri **ve dışarı aktarma** ayarları ' nı ** > seçerek** **Ayarları içeri ve dışarı aktarma Sihirbazı**' nı açın. **Tüm ayarları Sıfırla** ' yı seçin ve ardından sihirbazın kalan adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Ortam ayarları](../ide/environment-settings.md)
- [Ortam > hesapları seçenekleri iletişim kutusu](reference/accounts-environment-options-dialog-box.md)
