---
title: Visual Studio için erişilebilirlik ipuçları ve püf noktaları
description: Tümleşik geliştirme ortamını (IDE) engelli kişiler Visual Studio herkesin kullanımına daha erişilebilir hale geçirmeye yardımcı olacak ipuçları ve püf noktaları hakkında daha fazla bilgi edinin.
ms.date: 02/01/2022
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e33525aafac7cbb9c98667a070af58f17c3916f8
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951588"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio için erişilebilirlik ipuçları ve püf noktaları

Visual Studio ekran okuyucularla ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. İster IDE'de gezinmek için klavye kısayollarını kullanmak ister görünürlüğü artırmak için yüksek karşıtlıklı temaları kullanmak istemeden, bu sayfada bunun nasıl & püf noktalarıyla ilgili birkaç ipucu bulabilirsiniz.

Ayrıca, kodunuzla ilgili yararlı bilgileri ortaya çıkarmak için ek açıklamaları kullanma ve derleme ve kesme noktası olayları için sesli ipuçları ayarlama hakkında da bilgi edinebilirsiniz.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için bkz[. Mac için Visual Studio](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>IDE ayarlarınızı kaydetme

Pencere düzeninizi, klavye eşleme düzeninizi ve diğer tercihlerinizi kaydederek IDE deneyiminizi özelleştirebilirsiniz. Daha fazla bilgi için bkz[. IDE'Visual Studio kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>IDE'nizi yüksek karşıtlıklı görüntüleme için değiştirme

Bazı insanlar için bazı renkleri görmek daha zordur. Kod olarak daha fazla karşıtlık almak ancak tipik "Yüksek Karşıtlık" temalarını kullanmak istemiyorsanız, artık bir "Mavi (Ek Karşıtlık)" teması sunuyoruz.

  ![Mavi temayı ve Mavi Ek Karşıtlık temasını karşılaştırma](media/blue-extra-contrast-theme.png "Mavi temanın ve mavi ekstra kontrast temasının karşılaştırmasını gösteren ekran görüntüsü")

::: moniker range="vs-2022"

> [!TIP]
> Renk karşıtlığı oranı ayarlamaları ve yeni Cascadia Code yazı tipi hakkında daha fazla bilgi edinmek için kullanıcı arabirimini [**Visual Studio 2022'de**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) yükselttik blog gönderisi ve daha kolay erişilebilir hale Visual Studio için yeni bir Cascadia Code yazı tipine bakın.

::: moniker-end

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Kodunuzla ilgili yararlı bilgileri ortaya çıkarmak için ek açıklamaları kullanma

Visual Studio düzenleyicisi, bir kod satırı üzerinde belirli noktalarda bulunan özellikler hakkında bilgi vermenin yanı sıra tornavida ve ampul simgeleri, hata ve uyarı "dalgalı çizgi" ve yer işaretleri gibi birçok metin "donatma" özelliği içerir. "Satır Ek Açıklamalarını Göster" komut kümelerini kullanarak bu donatmaları keşfetmenize ve bunlar arasında gezinmenize yardımcı olabilir.

  ![Satır Ek Açıklamalarını Göster komut kümesi kullanma](media/show-line-annotations-command-set.png "Satır göster ek açıklamaları menü öğesinin ekran görüntüsü")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak araç çubuklarına erişme

IDE Visual Studio de birçok araç penceresinin olduğu gibi araç çubukları vardır. Aşağıdaki klavye kısayolları bu kısayollara erişmenizi sağlar.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE araç çubukları|Standart araç çubuğunda ilk düğmeyi seçin.|**Alt**, **CtrlTab**+|
|Araç penceresi araç çubukları|Odağı bir araç penceresindeki araç çubuklarına taşıma. <br> <br> **NOT:** Bu, çoğu araç penceresi için ancak odak bir araç penceresinde olduğunda çalışır. Ayrıca ALT anahtarı öncesinde SHIFT tuşunu seçmeniz gerekir. Alt tuşunu seçmeden önce Takım Gezgini gibi bazı araç pencerelerde SHIFT tuşunu bir süre tutmanız gerekir.|**Üstkrkt**+ **Alt**|
|Araç Çubukları|Sonraki araç çubuğundaki ilk öğeye gidin (araç çubuğunda odak olduğunda).|**Ctrl**+ **Sekme**|

### <a name="other-useful-keyboard-shortcuts"></a>Diğer kullanışlı klavye kısayolları

Diğer yararlı klavye kısayollarının bazıları şunlardır.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE|Anahtar Yüksek Karşıtlık ve kapatın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Sol Alt**+ **Sola Kaydırma**+ **Prtscn**|
|İletişim kutusu|İletişim kutusundaki onay kutusu seçeneğini belirleyin veya işaretini kaldırın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Boşluk çubuğu**|
|Bağlam menüleri|Bağlam (sağ tıklama) menüsünü açın. <br> <br> **NOT:** Standart Windows klavye kısayolu|**Üstkrkt**+ **F10**|
|Menüler|Kısayol tuşlarını kullanarak bir menü öğesini hızla erişin. Komutu **etkinleştirmek için** Alt tuşuna ve ardından menüde altı çizili harfler'i seçin. Örneğin, Bir Project aç iletişim kutusunu Visual Studio **AltFOP'yi**++ **seçebilirsiniz**+.  <br><br> **NOT:** Standart Windows klavye kısayolu|**Alt** +  **[letter]**|
|Arama kutusu|Visual Studio'da arama özelliğini kullanın.|**Ctrl**+ **S**|
|Araç kutusu penceresi|Araç Kutusu sekmeleri arasında taşıma.|**Ctrl**+ **Yukarı ok**<br /><br /> ve<br /><br /> **Ctrl**+ **Aşağı ok**|
|Araç kutusu penceresi|Araç Kutusundan bir forma veya tasarımcıya denetim ekleyin.|**Enter**|
|Seçenekler iletişim kutusu: Ortam > Klavye|Kısayol tuşlarına basın seçeneğine girilen **bir tuş bileşimini** silin.|**Geri Al tuşu**|
|Bildirimler araç penceresi|İki klavye kısayolu tuş bileşimini ve ardından diğer tuş bileşimini kullanarak Bildirimler araç penceresini açın. Ardından ok tuşlarını kullanarak bir bildirimi görüntüden seçin.| **Ctrl**+ **&#92;**, **CtrlN**+|

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak bildirimlere erişme

IDE'de bir bildirim görüntülendiğinde, klavye kısayollarını kullanarak Bildirimler penceresine şu şekilde erişebilirsiniz:

1. IDE'nin herhangi bir yerinde sırayla, sırayla aşağıdaki iki klavye kısayolu tuşlarına basın: **Ctrl**+**&#92;** ve **ardından CtrlN**+.

   Bildirimler **penceresi** açılır.

   ![IDE'de bildirimler Visual Studio penceresi](media/toast-notification.png "Visual Studio ıde 'de bildirimler penceresinin ekran görüntüsü")

1. Bildirim seçmek **için Sekme** tuşunu veya ok tuşlarını kullanın.

## <a name="use-the-sound-dialog-box-to-set-build-and-breakpoint-cues"></a>Derleme ve kesme noktası ipuçlarını ayarlamak için Ses iletişim kutusunu kullanma

Program olaylarında ses atamak için Windows iletişim kutusunu Visual Studio kullanabilirsiniz. Özellikle, aşağıdaki program olaylarını ses atabilirsiniz:

* Kesme noktası isabeti
* Derleme iptal edildi
* Derleme başarısız oldu
* Derleme başarılı oldu

Burada 11 veya daha büyük bir Windows program olaylarını Windows 10.

### <a name="windows-11"></a>Windows 11

1. Windows 11 çalıştıran bir bilgisayarda Başlat düğmesini seçin ve **ardından Arama** kutusuna Sistem seslerini değiştir **yazın**.

    :::image type="content" source="media/change-system-sounds-windows-11.png" alt-text="Windows 11'de Arama kutusunun ekran görüntüsü.":::

1. Arama sonuçlarından Sistem seslerini Denetim Masası seçeneğini **belirleyin**. (Alternatif olarak, **arama sonuçlarının** sağ panelinde Aç simgesini seçin.)

    :::image type="content" source="media/select-change-system-sounds-windows-11.png" alt-text="Windows 11'de 'Sistem seslerini değiştir' arama sonuçlarının ekran görüntüsü.":::

1. **Ses** iletişim kutusunda, **sesler** sekmesine tıklayın.

1. **Program olayları**' nda, **Microsoft Visual Studio**' ye kaydırın ve seçtiğiniz olaylara uygulamak istediğiniz sesleri seçin.

    :::image type="content" source="media/system-sounds-dialog-windows-11-.png" alt-text="Windows 11 ' de ses iletişim kutusunun sesler sekmesinin ekran görüntüsü.":::

1. **Tamam**'a tıklayın.

### <a name="windows-10"></a>Windows 10

1. Windows 10 çalıştıran bir bilgisayardaki **arama** kutusunda, **sistem seslerini değiştir** yazın.

   ![Windows 10 arama kutusu](media/type-here-to-search.png "Windows 10 arama kutusunun ekran görüntüsü")

   (alternatif olarak, Cortana etkinse, "Hey Cortana" deyin ve "sistem seslerini değiştirme" deyin.

1. **Sistem seslerini Değiştir**' e çift tıklayın.

   ![Windows 10 arama sonuçları](media/change-system-sounds.png "' Sistem seslerini Değiştir ' arama sonuçlarının Windows 10 ekran görüntüsü")

1. **Ses** iletişim kutusunda, **sesler** sekmesine tıklayın.

1. **Program olayları**' nda, **Microsoft Visual Studio**' ye kaydırın ve seçtiğiniz olaylara uygulamak istediğiniz sesleri seçin.

   ![Windows 10 Ses iletişim kutusunun sesler sekmesi](media/sound-applet.png "Windows 10 Ses iletişim kutusunun sesler sekmesi")

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
