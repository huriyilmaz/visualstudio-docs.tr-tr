---
title: Ayarları eşitle
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566793"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Visual Studio ayarlarını birden çok bilgisayarda eşitle

Aynı kişiselleştirme hesabını kullanarak birden çok bilgisayarda Visual Studio'da oturum açtığınızda, ayarlarınız bilgisayarlar arasında eşitlenebilir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar

Varsayılan olarak, aşağıdaki ayarlar eşitlenir:

- Geliştirme ayarları. Visual Studio'yu ilk açtığınızda bir ayarlar koleksiyonu seçersiniz, ancak seçimi istediğiniz zaman değiştirebilirsiniz. Daha fazla bilgi için [Çevre ayarlarına](../ide/environment-settings.md)bakın.

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarını nasıl tanımları hakkında daha fazla bilgi için [Visual Studio komut diğer adlarına](../ide/reference/visual-studio-command-aliases.md)bakın.

- **Pencere** > Yönet Penceresi Düzenleri sayfasında kullanıcı tanımlı pencere**düzenleri.**

- **Araç** > **Seçenekleri** sayfalarında aşağıdaki seçenekler:

  - **Ortam** > **Geneli** seçenekleri sayfasında tema ve menü çubuğu kaplama ayarları.

  - **Çevre** > **Yazı Tipleri ve Renkler** seçenekleri sayfasındaki tüm ayarlar.

  - **Çevre** > **Klavyesi** seçenekleri sayfasındaki tüm klavye kısayolları.

  - **Çevre** > **Sekmeleri ve Windows** seçenekleri sayfasındaki tüm ayarlar.

  - **Çevre** > **Başlangıç** seçenekleri sayfasındaki tüm ayarlar.

  - **Metin Düzenleyicisi** seçenekleri sayfalarındaki tüm ayarlar, örneğin kod [stili tercihleri.](code-styles-and-code-cleanup.md)

  - **XAML Designer** seçenekleri sayfalarındaki tüm ayarlar.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Belirli bir bilgisayarda eşitlenmiş ayarları kapatma

Visual Studio için senkronize ayarlar varsayılan olarak açık. **Araçlar** > **Seçenekleri** > **Çevre** > **Hesapları** sayfasına giderek bilgisayardaki senkronize ayarları kapatabilir ve Visual **Studio'da oturum açtığınızda cihazlar arasında senkronize ayarlarını açabilirsiniz.**

Örnek olarak, Visual Studio'nun ayarlarını "A" bilgisayarında eşitlememeye karar verirseniz, "A" bilgisayarında yapılan ayarlardaki değişiklikler "B" veya "C" bilgisayarında görünmez. "B" ve "C" bilgisayarları birbirleriyle eşitolmaya devam edecektir, ancak "A" bilgisayarıyla eşitlemeyapmaya devam edecektir.

> [!NOTE]
> **Araçlar** > **Seçenekleri** > **Çevre** > **Hesapları** sayfasındaki seçeneği deleyerek ayarları eşitlememeyi seçerseniz, aynı bilgisayarda bulunan Visual Studio'nun diğer sürümleri veya sürümleri etkilenmez. Visual Studio'nun yan yana yüklemeleri ayarlarını eşitlemeye devam eder (oradaki seçeneğin de işaretlerini kaldırmadığınız sürece).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio aile ürünleri ve sürümleri nde ayarları senkronize etme

Ayarlar, Visual Studio'nun *yan yana*yüklenen sürümleri ve sürümleri arasında senkronize edilir. Ayarlar, Visual Studio için Blend de dahil olmak üzere Visual Studio aile ürünleri arasında da senkronize edilir. Ancak, tek bir aile ürünü Visual Studio ile paylaşılmaz kendi ayarları olabilir. Örneğin, "A" bilgisayarında Visual Studio için Blend'e özgü ayarlar Visual Studio ile "A" veya "B" bilgisayarlarda paylaşılmaz.

## <a name="side-by-side-synchronized-settings"></a>Yan yana senkronize ayarlar

::: moniker range="vs-2017"

Araç penceresi düzeni gibi belirli ayarlar Visual Studio'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%userprofile%\Documents\Visual Studio 2017\Settings'teki* *CurrentSettings.vssettings* dosyası , *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*'e benzer bir yüklemeye özgü klasörde bulunmaktadır.

> [!NOTE]
> Yeni yüklemeye özgü ayarları kullanmak için yeni bir yükleme yapın. Varolan bir Visual Studio yüklemesini yükselttidiğinizde, varolan paylaşılan konumu kullanır.

Şu anda Visual Studio'nun yan yana yüklemeleri varsa ve yeni yüklemeye özgü ayarlar dosya konumunu kullanmak istiyorsanız, aşağıdaki adımları izleyin:

1. Visual Studio 2017 sürümü15.3 veya sonraki sürümüne yükseltin.

2. Varolan tüm ayarlarınızı *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* klasörünün dışında bir konuma aktarmak için **İçe Ve Dışa Aktar Ayarları** Sihirbazı'nı kullanın.

3. VS **2017 için Geliştirici Komut Komut Komut Ustem'ini** açın ve çalıştırın. `devenv /resetuserdata`

1. Visual Studio'yu açın ve kaydedilen ayarları dışa aktarılan ayarlar dosyasından alın.

::: moniker-end

::: moniker range=">=vs-2019"

Araç penceresi düzeni gibi belirli ayarlar Visual Studio'nun farklı yan yana yüklemeleri arasında paylaşılmaz. *%userprofile%\Documents\Visual Studio 2019\Settings'teki* *CurrentSettings.vssettings* dosyası , *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*'a benzer bir yüklemeye özgü klasördedir.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Senkronize ayarları sıfırlama

Tüm ayarları varsayılanlarına göre sıfırlamak için Visual Studio'da oturum açın ve ardından **İçe Ve Dışa**Aktar Ayarları Sihirbazı'nı açmak için **Araçlar** > **İçe Ve Dışa Aktar Ayarlarını** seçin. **Tüm ayarları Sıfırla'yı** seçin ve ardından sihirbazın kalan adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirin](../ide/personalizing-the-visual-studio-ide.md)
- [Ortam ayarları](../ide/environment-settings.md)
- [Çevre > Hesaplar Seçenekleri iletişim kutusu](reference/accounts-environment-options-dialog-box.md)
