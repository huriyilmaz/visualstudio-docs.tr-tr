---
title: Ayarları eşitleme
description: Aynı kişiselleştirme hesabında oturum Visual Studio birden çok bilgisayar arasında uygulama ayarlarınızı eşitlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/18/2020
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 360db67aa0daf09916ae21c9cd1028c0a285e35b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048459"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Birden Visual Studio bilgisayar arasında eşitleme ayarları

Aynı kişiselleştirme hesabı Visual Studio birden çok bilgisayarda oturum asanız, ayarlarınız bilgisayarlar arasında eşitlenir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar

Varsayılan olarak, aşağıdaki ayarlar eşitlenir:

- Geliştirme ayarları. İlk kez bir ayar koleksiyonu seçerek Visual Studio istediğiniz zaman değiştirebilirsiniz. Daha fazla bilgi için [bkz. Ortam ayarları.](../ide/environment-settings.md)

- Kullanıcı tanımlı komut diğer adları. Komut diğer adlarını tanımlama hakkında daha fazla bilgi için [bkz. Visual Studio diğer adları.](../ide/reference/visual-studio-command-aliases.md)

- Pencere Düzenlerini Yönet **sayfasındaki**  >  **kullanıcı tanımlı pencere** düzenleri.

- Araçlar Seçenekler sayfalarındaki **aşağıdaki**  >  **seçenekler:**

  - Ortam Genel seçenekleri sayfasındaki tema ve menü **çubuğu büyük/büyük/büyük/yeni**  >   ayarlar.

  - Ortam Yazı Tipleri **ve Renkler**  >  **seçenekleri sayfasındaki tüm** ayarlar.

  - Ortam Klavye seçenekleri **sayfasındaki**  >  **tüm klavye** kısayolları.

  - Ortam Sekmeleri ve  >  **Sekmeler sayfasındaki Windows** ayarlar.

  - Ortam Başlangıç seçenekleri  >  **sayfasındaki tüm** ayarlar.

  - Metin Düzenleyici seçenekleri **sayfalarındaki** tüm ayarlar, örneğin, [kod stili tercihleri.](code-styles-and-code-cleanup.md)

  - Uygulama seçenekleri **sayfalarındaki XAML Tasarımcısı** ayarlar.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Belirli bir bilgisayarda eşitlenen ayarları kapatma

Eşitleme ayarları Visual Studio olarak açıktır. Araçlar Seçenekler Ortam Hesapları sayfasına gidip Visual Studio'de oturum asanız cihazlar arasında ayarları eşitle'nin işaretini kaldırarak bir bilgisayarda   >    >    >   **eşitlenen ayarları kapatabilirsiniz.**

Örneğin, "A" bilgisayarına Visual Studio ayarları eşitlemeye karar verdiyseniz, "A" bilgisayarda yapılan tüm ayar değişiklikleri "B" bilgisayarda veya "C" bilgisayarda görünmez. "B" ve "C" bilgisayarları "A" bilgisayarıyla değil, diğerleriyle eşitlemeye devam eder.

> [!NOTE]
> Araçlar Seçenekler Ortam Hesapları sayfasındaki seçeneğin seçimini kaldırarak ayarları eşitlemezseniz, aynı bilgisayarda sahip Visual Studio diğer sürümler veya sürümleri  >    >    >   etkilenmez. Bu yan yana yüklemeleri Visual Studio ayarlarını eşitlemeye devam eder (burada seçeneğin işaretini de kaldırmayacaksanız).

## <a name="synchronize-settings-across-visual-studio-ide-products-and-editions"></a>IDE ürünleri Visual Studio sürümleri arasında ayarları eşitleme

Ayarlar yan yana yüklü olan Visual Studio sürümleri *arasında eşitlenir.* Ayarlar, IDE ürünleri dahil olmak Visual Studio IDE ürünleri arasında da Visual Studio için Blend. Ancak, IDE Visual Studio tek bir ürün, IDE ürünüyle paylaşılmadan kendi ayarlarına Visual Studio. Örneğin, "A" Visual Studio için Blend bilgisayara özgü ayarlar "A" Visual Studio "B" bilgisayarlarla paylaşılmaz.

## <a name="side-by-side-synchronized-settings"></a>Yan yana eşitlenen ayarlar

::: moniker range="vs-2017"

Araç penceresi düzeni gibi bazı ayarlar, uygulamanın farklı yan yana yüklemeleri arasında Visual Studio. *%userprofile%\Documents\Visual Studio 2017\Ayarlar* konumundaki *CurrentSettings.vssettings* dosyası *, %localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Ayarlar* ile benzer bir yüklemeye özgü klasördedir.

> [!NOTE]
> Yüklemeye özgü yeni ayarları kullanmak için yeni bir yükleme yapın. Mevcut bir uygulama yüklemesini Visual Studio, mevcut paylaşılan konumu kullanır.

Şu anda bir uygulamanın yan yana yüklemeleri Visual Studio ve yüklemeye özgü yeni ayarlar dosya konumunu kullanmak için şu adımları izleyin:

1. 2017 Visual Studio 15.3 veya sonraki bir sürüme yükseltin.

2. Tüm mevcut **Ayarlar ayarlarınızı** *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* klasörünün dışındaki bir konuma dışarı aktarın.

3. VS **2017 için Geliştirici Komut İstemi'i açın ve** `devenv /resetuserdata` çalıştırın.

1. Dosyayı Visual Studio ve dışarı aktaran ayarlar dosyasından kaydedilen ayarları içeri aktarın.

::: moniker-end

::: moniker range=">=vs-2019"

Araç penceresi düzeni gibi bazı ayarlar, uygulamanın farklı yan yana yüklemeleri arasında Visual Studio. *%userprofile%\Documents\Visual Studio 2019\Ayarlar* konumundaki *CurrentSettings.vssettings* dosyası *, %localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Ayarlar* ile benzer bir yüklemeye özgü klasördedir.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Eşitlenen ayarları sıfırlama

Tüm ayarları varsayılan ayarlarına sıfırlamak için, Visual Studio'de oturum açın ve ardından Araçlar İçeri ve Dışarı Aktarma Ayarlar'nı seçerek İçeri ve Dışarı Aktarma  >   **sihirbazını Ayarlar açın.** Tüm **ayarları sıfırla'yı** seçin ve sihirbazın kalan adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Ortam ayarları](../ide/environment-settings.md)
- [Ortam > Hesapları Seçenekleri iletişim kutusu](reference/accounts-environment-options-dialog-box.md)
- [Visual Studio sürümlerini yan yana yükleme](../install/install-visual-studio-versions-side-by-side.md)
