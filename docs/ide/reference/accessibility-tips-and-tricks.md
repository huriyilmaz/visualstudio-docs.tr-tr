---
title: Visual Studio için erişilebilirlik ipuçları ve püf noktaları
description: Visual Studio entegre geliştirme ortamını (IDE) engelli kişiler de dahil olmak üzere herkesin kullanabileceği daha erişilebilir hale getirmeye yardımcı olabilecek ipuçları ve püf noktaları hakkında daha fazla bilgi edinin.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5828fb114a4df559c46dd6ae7f64887ab48e7429
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68919531"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio için erişilebilirlik ipuçları ve püf noktaları

Visual Studio, ekran okuyucular ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. IDE'de gezinmek için klavye kısayollarını kullanmak veya görünürlüğü artırmak için yüksek kontrastlı temalar kullanmak istiyorsanız, bu sayfada bunu nasıl yapacağınız hakkında çeşitli ipuçları & hileler bulacaksınız.

Ayrıca, kodunuz hakkında yararlı bilgileri ortaya çıkarmak için ek açıklamaların nasıl kullanılacağını ve yapı ve kesme noktası olayları için ses ipuçlarının nasıl ayarlanıştını da kapsarız.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio için Erişilebilirlik'e](/visualstudio/mac/accessibility)bakın.

## <a name="save-your-ide-settings"></a>IDE ayarlarınızı kaydedin

Pencere düzeninizi, klavye eşleme düzeninizi ve diğer tercihlerinizi kaydederek IDE deneyiminizi özelleştirebilirsiniz. Daha fazla bilgi için [Visual Studio IDE'yi Kişiselleştir'e](../../ide/personalizing-the-visual-studio-ide.md)bakın.

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Yüksek kontrastlı görüntüleme için IDE'nizi değiştirin

Bazı millet için, bazı renkleri görmek daha zordur. Kod olarak daha fazla kontrast istiyorsanız ancak tipik "Yüksek Karşıtlık" temalarını kullanmak istemiyorsanız, şimdi bir "Mavi (Ekstra Kontrast)" teması sunuyoruz.

  ![Mavi teonu ve Mavi Ekstra Kontrast tesini karşılaştırın](media/blue-extra-contrast-theme.png "Mavi tema ve Mavi Ekstra Kontrast temasının karşılaştırmasını gösteren ekran görüntüsü")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Kodunuz hakkında yararlı bilgileri ortaya çıkarmak için ek açıklamaları kullanma

Visual Studio editörü, tornavida ve ampul simgeleri, hata ve uyarı "squiggles", yer imleri, ve benzeri gibi kod bir satır üzerinde belirli noktalarda özellikleri ve özellikleri hakkında bildirmek birçok metin "süslemeleri" içerir. Bu süslemeleri keşfetmenize ve daha sonra bu süslemeler arasında gezinmenize yardımcı olmak için "Çizgi Ek Açıklamalarını Göster" kümesini kullanabilirsiniz.

  ![Çizgi Ek Açıklamaları Göster komut kümesini kullanma](media/show-line-annotations-command-set.png "Çizgi Ek Açıklamaları Göster menü öğesinin ekran görüntüsü")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak araç çubuklarına erişin

Visual Studio IDE'de birçok araç penceresi gibi araç çubukları vardır. Aşağıdaki klavye kısayolları bunlara erişmenize yardımcı olur.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE araç çubukları|Standart araç çubuğundaki ilk düğmeyi seçin.|**Alt**, **Ctrl**+**Sekmesi**|
|Araç penceresi araç çubukları|Odak noktasını araç penceresindeki araç çubuklarına taşıyın. <br> <br> **NOT:** Bu, çoğu araç penceresi için çalışır, ancak yalnızca odak bir araç penceresinde olduğunda. Ayrıca, ALT tuşu önce SHIFT tuşunu seçmeniz gerekir. Team Explorer gibi bazı araç pencerelerinde, ALT anahtarını seçmeden önce SHIFT tuşunu bir an süre tutmanız gerekir.|**Vardiya**+**Alt**|
|Araç Çubukları|Sonraki araç çubuğundaki ilk öğeye gidin (araç çubuğunda odak noktası olduğunda).|**Ctrl**+**Sekmesi**|

### <a name="other-useful-keyboard-shortcuts"></a>Diğer kullanışlı klavye kısayolları

Diğer bazı yararlı klavye kısayolları şunlardır.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE|Yüksek Karşıtlığı açıp kapatın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Sol Alt**+**Sol Shift**+**PrtScn**|
|İletişim kutusu|İletişim kutusundaonay kutusu seçeneğini seçin veya temizleyin. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Boşluk çubuğu**|
|Bağlam menüleri|Bağlam (sağ tıklatma) menüsünü açın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Shift**+**F10**|
|Menüler|Hızlandırıcı tuşlarını kullanarak bir menü öğesine hızla erişin. Komutu etkinleştirmek için menüdeki altı çizili harflerin ardından **Alt** tuşunu seçin. Örneğin, Visual Studio'da Proje Aç iletişim kutusunu görüntülemek için **Alt**+**F**+**O**+**P'yi**seçersiniz.  <br><br> **NOT:** Standart Windows klavye kısayolu|**Alt** + **[mektup]**|
|Arama kutusu|Visual Studio'daki arama özelliğini kullanın.|**Ctrl**+**Q**|
|Araç kutusu penceresi|Araç Kutusu sekmeleri arasında taşıyın.|**Ctrl**+**Yukarı ok**<br /><br /> ve<br /><br /> **Ctrl**+**Aşağı ok**|
|Araç kutusu penceresi|Araç Kutusundan bir forma veya tasarımcıya denetim ekleyin.|**Enter**|
|Seçenekler iletişim kutusu: Ortam > Klavye|**Basın kısayol tuşları** seçeneğine girilen bir tuş kombinasyonunu silin.|**Geri Al tuşu**|
|Bildirimler araç penceresi|Biri diğeri olmak üzere iki klavye kısayol tuşu birleşimi kullanarak Bildirimler araç penceresini açın. Ardından, seçmek için ok tuşlarını kullanarak bir bildirimi görüntüleyin.| **Ctrl** + **&#92;**, **Ctrl**+**N**|

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürüme bağlı olarak Yardım'da açıklananlardan farklı olabilir.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak bildirimlere erişin

IDE'de bir bildirim görüntülendiğinde, klavye kısayollarını kullanarak Bildirimler penceresine şu şekilde erişebilirsiniz:

1. IDE'nin herhangi bir yerinden, aşağıdaki iki klavye kısayollarına sırayla, birbiri ardına basın: **Ctrl** + **&#92;** ve ardından **Ctrl**+**N**.

   **Bildirimler** penceresi açılır.

   ![Visual Studio IDE'deki Bildirimler araç penceresi](media/toast-notification.png "Visual Studio IDE'deki Bildirimler penceresinin ekran görüntüsü")

1. Bir bildirim seçmek için **Sekme** tuşunu veya ok tuşlarını kullanın.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Yapı ve kesme noktası ipuçlarını ayarlamak için Ses elmasını kullanın

Visual Studio program etkinliklerine ses atamak için Windows'daki Ses uygulamasını kullanabilirsiniz. Özellikle, sesleri aşağıdaki program olaylarına atayabilirsiniz:

* Breakpoint isabet
* Yapı iptal edildi
* Yapı başarısız oldu
* Yapı başarılı

Bunu yapmak için:

1. Windows 10 çalıştıran bir bilgisayardaki **Arama** kutusunda, **sistem seslerini**değiştir yazın.

   ![Windows 10'da arama kutusu](media/type-here-to-search.png "Windows 10'da Arama kutusunun ekran görüntüsü")

   (Alternatif olarak, Cortana etkinleştirilmişse, "Hey Cortana" deyin ve ardından "Sistem seslerini değiştirin" deyin.)

1. Çift tıklatma **Sistem sesleri değiştir.**

   ![Windows 10'da arama sonuçları](media/change-system-sounds.png "Windows 10'da 'Sistem seslerini değiştir' arama sonuçlarının ekran görüntüsü")

1. **Ses** iletişim **kutusunda, Sesler** sekmesini tıklatın.

1. **Program**Etkinlikleri'nde, Microsoft **Visual Studio'ya**gidin ve ardından seçtiğiniz etkinliklere uygulamak istediğiniz sesleri seçin.

   ![Windows 10'da Ses elmasının sesleri sekmesi](media/sound-applet.png "Windows 10'da Ses elmasının sesleri sekmesi")

1. **Tamam**'a tıklayın.

::: moniker range="vs-2017"

> [!TIP]
> Erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi edinmek için [Visual Studio 2017 sürüm 15.3 blog gönderisinde Erişilebilirlik geliştirmelerine](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) bakın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Nasıl yapIlir: Visual Studio'da menüleri ve araç çubuklarını özelleştirin](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Visual Studio IDE'yi kişiselleştirin](../../ide/personalizing-the-visual-studio-ide.md)
* [Erişilebilirlik (Mac için Visual Studio)](/visualstudio/mac/accessibility)
* [Microsoft Erişilebilirlik](https://www.microsoft.com/Accessibility)
