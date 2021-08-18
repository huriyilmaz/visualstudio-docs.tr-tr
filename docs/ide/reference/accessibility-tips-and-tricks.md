---
title: Visual Studio için erişilebilirlik ipuçları ve püf noktaları
description: Tümleşik geliştirme ortamını (IDE) engelli kişiler de dahil olmak üzere herkesin kullanımına daha erişilebilir hale Visual Studio ipuçları ve püf noktaları hakkında daha fazla bilgi edinin.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 899d44ff13ae9c94309757363a96b814e5e3e531
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041356"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio için erişilebilirlik ipuçları ve püf noktaları

Visual Studio ekran okuyucularla ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. İster IDE'de gezinmek için klavye kısayollarını kullanmak ister görünürlüğü artırmak için yüksek karşıtlıklı temaları kullanmak istemeden, bu sayfada bunun nasıl & püf noktalarıyla ilgili birkaç ipucu bulabilirsiniz.

Ayrıca, kodunuzla ilgili yararlı bilgileri ortaya çıkarmak için ek açıklamaları kullanma ve derleme ve kesme noktası olayları için sesli ipuçları ayarlama hakkında da bilgi edinebilirsiniz.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/accessibility)

## <a name="save-your-ide-settings"></a>IDE ayarlarınızı kaydetme

Pencere düzeninizi, klavye eşleme düzeninizi ve diğer tercihlerinizi kaydederek IDE deneyiminizi özelleştirebilirsiniz. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="modify-your-ide-for-high-contrast-viewing"></a>IDE'nizi yüksek karşıtlıklı görüntüleme için değiştirme

Bazı insanlar için bazı renkleri görmek daha zordur. Kod olarak daha fazla karşıtlık almak ancak tipik "Yüksek Karşıtlık" temalarını kullanmak istemiyorsanız, artık bir "Mavi (Ek Karşıtlık)" teması sunuyoruz.

  ![Mavi temayı ve Mavi Ek Karşıtlık temasını karşılaştırma](media/blue-extra-contrast-theme.png "Mavi temanın ve mavi ekstra kontrast temasının karşılaştırmasını gösteren ekran görüntüsü")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Kodunuzla ilgili yararlı bilgileri ortaya çıkarmak için ek açıklamaları kullanma

Visual Studio düzenleyicisi, bir kod satırı üzerinde belirli noktalarda bulunan özellikler hakkında bilgi vermenin yanı sıra tornavida ve ampul simgeleri, hata ve uyarı "dalgalı çizgi" ve yer işaretleri gibi birçok "donatma" metni içerir. "Satır Ek Açıklamalarını Göster" komut kümelerini kullanarak bu donatmaları keşfetmenize ve bunlar arasında gezinmenize yardımcı olabilir.

  ![Satır Ek Açıklamalarını Göster komut kümesi kullanma](media/show-line-annotations-command-set.png "Satır göster ek açıklamaları menü öğesinin ekran görüntüsü")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak araç çubuklarına erişme

IDE Visual Studio de birçok araç penceresinin olduğu gibi araç çubukları vardır. Aşağıdaki klavye kısayolları bu kısayollara erişmenizi sağlar.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE araç çubukları|Standart araç çubuğunda ilk düğmeyi seçin.|**Alt**, **Ctrl** + **Tab**|
|Araç penceresi araç çubukları|Odağı bir araç penceresindeki araç çubuklarına taşıma. <br> <br> **NOT:** Bu, çoğu araç penceresi için ancak odak bir araç penceresinde olduğunda çalışır. Ayrıca ALT anahtarı öncesinde SHIFT tuşunu seçmeniz gerekir. Alt tuşunu seçmeden önce Takım Gezgini gibi bazı araç pencerelerde SHIFT tuşunu bir süre tutmanız gerekir.|**Shift ile kaydırma** + **Alt**|
|Araç Çubukları|Sonraki araç çubuğundaki ilk öğeye gidin (bir araç çubuğunda odak olduğunda).|**Ctrl tuşunu basılı tutarak** + **Sekme**|

### <a name="other-useful-keyboard-shortcuts"></a>Diğer kullanışlı klavye kısayolları

Diğer yararlı klavye kısayollarının bazıları şunlardır.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE|Düğmeyi Yüksek Karşıtlık ve kapatın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Sol Alt** + **Sola Kaydırma** + **PrtScn**|
|İletişim kutusu|İletişim kutusundaki onay kutusu seçeneğini belirleyin veya işaretini kaldırın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Boşluk çubuğu**|
|Bağlam menüleri|Bağlam (sağ tıklama) menüsünü açın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Shift ile kaydırma** + **F10**|
|Menüler|Kısayol tuşlarını kullanarak bir menü öğesini hızla erişin. Komutu **etkinleştirmek** için Alt tuşuna ve ardından menüde altı çizili harfler'i seçin. Örneğin, Dosya aç iletişim kutusunu Project için Visual Studio **F** O P seçeneğini +  +  + **belirleyebilirsiniz.**  <br><br> **NOT:** Standart Windows klavye kısayolu|**Alt**  +  **[letter]**|
|Arama kutusu|Arama özelliğini Visual Studio.|**Ctrl tuşunu basılı tutarak** + **Q**|
|Araç kutusu penceresi|Araç Kutusu sekmeleri arasında taşıma.|**Ctrl tuşunu basılı tutarak** + **Yukarı ok**<br /><br /> ve<br /><br /> **Ctrl tuşunu basılı tutarak** + **Aşağı ok**|
|Araç kutusu penceresi|Araç Kutusundan bir forma veya tasarımcıya denetim ekleyin.|**Enter**|
|Seçenekler iletişim kutusu: Ortam > Klavye|Kısayol tuşlarına basın seçeneğine girilen **bir tuş bileşimini** silin.|**Geri Al tuşu**|
|Bildirimler araç penceresi|İki klavye kısayolu tuş bileşimini ve ardından diğer tuş bileşimini kullanarak Bildirimler araç penceresini açın. Ardından ok tuşlarını kullanarak bir bildirimi görüntüden seçin.| **Ctrl tuşunu basılı tutarak** + **&#92;**, **Ctrl** + **N**|

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak bildirimlere erişme

IDE'de bir bildirim görüntülendiğinde, klavye kısayollarını kullanarak Bildirimler penceresine şu şekilde erişebilirsiniz:

1. IDE'nin herhangi bir yerinden sırayla aşağıdaki iki klavye kısayolu tuşlarına basın: **Ctrl** + **&#92;** ve **ardından Ctrl** + **N**.

   Bildirimler **penceresi** açılır.

   ![IDE'de bildirimler Visual Studio penceresi](media/toast-notification.png "Visual Studio ıde 'de bildirimler penceresinin ekran görüntüsü")

1. Bildirim seçmek **için Sekme** tuşunu veya ok tuşlarını kullanın.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Derleme ve kesme noktası ipuçlarını ayarlamak için Sound applet'ı kullanma

Program olaylarında ses atamak Windows ses applet'Visual Studio kullanabilirsiniz. Özellikle, aşağıdaki program olaylarını ses atabilirsiniz:

* Kesme noktası isabeti
* Derleme iptal edildi
* Derleme başarısız oldu
* Derleme başarılı oldu

Aşağıdaki adımları uygulayın:

1. Aşağıdakini **çalıştıran** bir bilgisayarda Arama kutusuna Windows 10 **seslerini değiştir yazın.**

   ![Windows 10'de arama kutusu](media/type-here-to-search.png "Windows 10 arama kutusunun ekran görüntüsü")

   (Alternatif olarak, "Hey Cortana" gibi bir Cortana ve ardından "Sistem seslerini değiştir" diyelim.)

1. Sistem seslerini **değiştir'e çift tıklayın.**

   ![Arama sonuçlarında Windows 10](media/change-system-sounds.png "' Sistem seslerini Değiştir ' arama sonuçlarının Windows 10 ekran görüntüsü")

1. Ses **iletişim** kutusunda, Sesler **sekmesine** tıklayın.

1. **Program Olayları'Microsoft Visual Studio** ekranı kaydırarak öğesini seçin ve ardından seçtiğiniz olaylara uygulamak istediğiniz sesleri seçin.

   ![Windows 10 Ses uygulamasının sesler sekmesi](media/sound-applet.png "Windows 10 Ses uygulamasının sesler sekmesi")

1. **Tamam**'a tıklayın.

::: moniker range="vs-2017"

> [!TIP]
> erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi edinmek için [Visual Studio 2017 sürüm 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisine bakın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Nasıl yapılır: Visual Studio menüleri ve araç çubuklarını özelleştirme](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
* [erişilebilirlik (Mac için Visual Studio)](/visualstudio/mac/accessibility)
* [Microsoft Erişilebilirlik](https://www.microsoft.com/Accessibility)
