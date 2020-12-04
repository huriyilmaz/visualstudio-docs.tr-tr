---
title: Ayarları eşitler
description: Aynı kişiselleştirme hesabında oturum açarak Visual Studio ayarlarınızı birden çok bilgisayar arasında eşitlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/18/2020
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 310e716f890dcc2185d6ebf6e60411934a1761f4
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560921"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Visual Studio ayarlarını birden çok bilgisayar arasında eşitler

Aynı kişiselleştirme hesabını kullanarak Visual Studio 'da birden çok bilgisayarda oturum açtığınızda, ayarlarınız bilgisayarlar arasında eşitlenebilir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar

Varsayılan olarak, aşağıdaki ayarlar eşitlenir:

- Geliştirme ayarları. Visual Studio 'Yu ilk kez açtığınızda bir ayarlar koleksiyonu seçersiniz, ancak seçimi dilediğiniz zaman değiştirebilirsiniz. Daha fazla bilgi için bkz. [ortam ayarları](../ide/environment-settings.md).

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarının nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

- **Pencere pencere**  >  **düzenlerini Yönet** sayfasında Kullanıcı tanımlı pencere düzenleri.

- **Araçlar**  >  **Seçenekler** sayfalarında aşağıdaki seçenekler:

  - **Ortam**  >  **genel** Seçenekler sayfasında Tema ve menü çubuğu büyük küçük harf ayarları.

  - **Ortam**  >  **yazı tipi ve renkler** seçenekleri sayfasındaki tüm ayarlar.

  - **Ortam**  >  **klavye** seçenekleri sayfasındaki tüm klavye kısayolları.

  - **Ortam**  >  **sekmeleri ve Windows** seçenekleri sayfasındaki tüm ayarlar.

  - **Ortam**  >  **başlatma** seçenekleri sayfasındaki tüm ayarlar.

  - **Metin düzenleyici** seçenekleri sayfalarındaki tüm ayarlar (örneğin, [kod stili tercihleri](code-styles-and-code-cleanup.md)).

  - **XAML Tasarımcısı** seçenekleri sayfalarındaki tüm ayarlar.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Belirli bir bilgisayardaki eşitlenmiş ayarları kapat

Visual Studio için eşitlenmiş ayarlar varsayılan olarak açıktır. Bir bilgisayardaki eşitlenmiş ayarları, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **hesapları** sayfasına gidip, **Visual Studio 'da oturum açıldığında cihazlarda ayarları eşitleme**' yi kaldırarak devre dışı bırakabilirsiniz.

Örnek olarak, "A" bilgisayarındaki Visual Studio 'daki ayarları eşitlememeye karar verirseniz, "A" bilgisayarında yapılan herhangi bir ayar değişikliği "B" bilgisayarında veya "C" bilgisayarında görünmez. "B" ve "C" bilgisayarları birbirleriyle eşitlemeye devam eder, ancak "A" bilgisayarıyla kalmaz.

> [!NOTE]
> Ayarları, **Araçlar**  >  **Seçenekler** ortam hesapları sayfasındaki seçeneğin seçimini kaldırarak eşitlemeiyorsanız  >  **Environment**  >  **Accounts** , Visual Studio 'nun aynı bilgisayardaki diğer sürümleri veya sürümleri etkilenmez. Visual Studio 'nun bu yan yana yüklemeleri, ayarlarını eşitlemeye devam edecektir (çok fazla onay işareti yoksa).

## <a name="synchronize-settings-across-visual-studio-ide-products-and-editions"></a>Visual Studio IDE ürünleri ve sürümleri üzerinde ayarları eşitler

Ayarlar, Visual Studio 'nun sürümleri *ve yan yana yüklenmiş olarak* eşitlenir. Ayrıca, Visual Studio için Blend da dahil olmak üzere Visual Studio IDE ürünleri arasında ayarlar eşitlenir. Ancak, Visual Studio IDE ürününün tek bir ürünü, Visual Studio ile paylaşılmayan kendi ayarlarına sahip olabilir. Örneğin, "A" bilgisayarındaki Visual Studio için Blend özgü ayarlar, "A" veya "B" bilgisayarlarında Visual Studio ile paylaşılmaz.

## <a name="side-by-side-synchronized-settings"></a>Yan yana eşitlenmiş ayarlar

::: moniker range="vs-2017"

Araç penceresi düzeni gibi bazı ayarlar, Visual Studio 'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%Userprofile%\, Studio 2017 \ Settings* Içindeki *Currentsettings. vssettings* dosyası, *%LocalAppData%\Microsoft\VisualStudio\ 15.0_xxxxxxxx \settings* ile benzer bir yüklemeye özgü klasördür.

> [!NOTE]
> Yüklemeye özgü yeni ayarları kullanmak için yeni bir yükleme yapın. Var olan bir Visual Studio yüklemesini yükselttiğinizde, mevcut paylaşılan konum kullanılır.

Şu anda Visual Studio 'nun yan yana yüklemelerine sahipseniz ve yüklemeye özgü yeni ayarlar dosya konumunu kullanmak istiyorsanız, aşağıdaki adımları izleyin:

1. Visual Studio 2017 sürüm 15,3 veya sonraki bir sürüme yükseltin.

2. Tüm mevcut ayarlarınızı *%localappdata%\microsoft\visualstudio\ 15.0_xxxxxxxx* klasörünün dışında bir konuma dışarı aktarmak Için **ayarları Içeri ve dışarı aktarma Sihirbazı 'nı** kullanın.

3. **VS 2017 için geliştirici komut istemi** açın ve çalıştırın `devenv /resetuserdata` .

1. Visual Studio 'Yu açın ve dışarı aktarılan ayarlar dosyasından kaydedilen ayarları içeri aktarın.

::: moniker-end

::: moniker range=">=vs-2019"

Araç penceresi düzeni gibi bazı ayarlar, Visual Studio 'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%Userprofile%\, Studio 2019 \ Settings* Içindeki *Currentsettings. vssettings* dosyası, *%LocalAppData%\Microsoft\VisualStudio\ 16.0_xxxxxxxx \settings* ile benzer bir yüklemeye özgü klasördür.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Eşitlenmiş ayarları Sıfırla

Tüm ayarları varsayılan değerlerine sıfırlamak için, Visual Studio 'da oturum açın ve ardından **Araçlar** içeri aktar ve dışarı aktar ayarları ' nı seçerek  >  **Import and Export Settings** **Ayarları içeri ve dışarı aktarma Sihirbazı**' nı açın. **Tüm ayarları Sıfırla** ' yı seçin ve ardından sihirbazın kalan adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Ortam ayarları](../ide/environment-settings.md)
- [Ortam > hesapları seçenekleri iletişim kutusu](reference/accounts-environment-options-dialog-box.md)
- [Visual Studio sürümlerini yan yana yükleme](../install/install-visual-studio-versions-side-by-side.md)
