---
title: Visual Studio için erişilebilirlik ipuçları ve püf noktaları
description: Visual Studio tümleşik geliştirme ortamının (ıde) herkesin kullanması için daha erişilebilir hale getirmenize yardımcı olabilecek ipuçları ve püf noktaları hakkında daha fazla bilgi edinin.
ms.date: 11/03/2021
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
ms.openlocfilehash: f9db3da41e1509d246bc51798f3e8751a3bcf569
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977854"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio için erişilebilirlik ipuçları ve püf noktaları

Visual Studio, ekran okuyucular ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. IDE 'de gezinmek için klavye kısayollarını kullanmak veya görünürlüğü geliştirmek için yüksek karşıtlıklı temalar kullanmak isteyip istemediğiniz, bu sayfada bunun nasıl yapılacağı hakkında birkaç & ipucu bulacaksınız.

Ayrıca, kodunuzun hakkındaki yararlı bilgileri göstermek için ek açıklamaların nasıl kullanılacağını ve derleme ve kesme noktası olayları için ses ipuçları ayarlamayı da ele aldık.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio için erişilebilirlik](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>IDE ayarlarınızı kaydetme

Pencere düzeninizi, klavye eşleme düzeninizi ve diğer Tercihlerinizi kaydederek IDE deneyiminizi özelleştirebilirsiniz. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>IDE 'nizi yüksek karşıtlıklı görüntüleme için değiştirme

Bazı katlara, bazı renklerin görülmesi daha zordur. Kodlarken, ancak tipik "Yüksek Karşıtlık" temalarını kullanmak istemediğinizde daha fazla karşıtlık isterseniz, artık "mavi (ekstra Karşıtlık)" teması sunuyoruz.

  ![Mavi temayı ve mavi ekstra Karşıtlık temasını karşılaştırın](media/blue-extra-contrast-theme.png "Mavi temanın ve mavi ekstra kontrast temasının karşılaştırmasını gösteren ekran görüntüsü")

::: moniker range="vs-2022"

> [!TIP]
> hafif renk karşıtlığı oranı ayarlamaları hakkında daha fazla bilgi edinmek için [**Visual Studio 2022 blog postasında kullanıcı arabirimini yükselttik**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) ve Visual Studio herkes için daha erişilebilir hale getirmek üzere eklediğimiz yeni bir basamaklı dia kodu yazı tipi hakkında daha fazla bilgi edinmek için bkz..

::: moniker-end

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Kodunuzla ilgili yararlı bilgileri açığa çıkarmak için ek açıklamaları kullanın

Visual Studio düzenleyicisi, screwsürücü ve ampul simgeleri, hata ve uyarı "dalgalı çizgiler", yer işaretleri vb. gibi bir kod satırı üzerinde belirli noktalarda özellikler ve özellikler hakkında bilgi sahibi olan "donnments" adlı birçok metni içerir. "Satır ek açıklamalarını göster" komut kümesini kullanarak bu donatıcılıkları bulmanıza ve sonra gezinmenize yardımcı olun.

  ![Satır ek açıklamalarını göster komut kümesini kullanın](media/show-line-annotations-command-set.png "Satır göster ek açıklamaları menü öğesinin ekran görüntüsü")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak araç çubuklarına erişin

Visual Studio ıde 'nin birçok araç penceresi gibi araç çubukları vardır. Aşağıdaki klavye kısayolları bunlara erişmenize yardımcı olur.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE araç çubukları|Standart araç çubuğunda ilk düğmeyi seçin.|**Alt**, **CTRL** + **sekmesi**|
|Araç penceresi araç çubukları|Odağı bir araç penceresinde araç çubuklarına taşıyın. <br> <br> **Note:** Bu, çoğu araç penceresi için geçerlidir, ancak yalnızca odak bir araç penceresidir. Ayrıca, ALT anahtardan önce SHIFT tuşunu seçmeniz gerekir. Takım Gezgini gibi bazı araç pencerelerinin ALT tuşunu seçmeden önce bir süre için SHIFT tuşunu basılı tutmanız gerekir.|**SHIFT** + **Alt**|
|Araç Çubukları|Sonraki araç çubuğunda ilk öğeye git (bir araç çubuğu odağa sahip olduğunda).|**CTRL** + **Sekme**|

### <a name="other-useful-keyboard-shortcuts"></a>Diğer faydalı klavye kısayolları

Diğer bazı faydalı klavye kısayolları aşağıdakileri içerir.

|Özellik|Açıklama|Klavye kısayolu|
|-------------|-----------------| - |
|IDE|Yüksek Karşıtlık açma ve kapatma. <br> <br> **Note:** standart Windows klavye kısayolu|**Sol alt** + **Sola kaydırma** + **PrtScn**|
|İletişim kutusu|İletişim kutusunda onay kutusu seçeneğini belirleyin veya temizleyin. <br> <br> **Note:** standart Windows klavye kısayolu|**Boşluk çubuğu**|
|Bağlam menüleri|Bir bağlam açın (sağ tıklama) menüsü. <br> <br> **Note:** standart Windows klavye kısayolu|**SHIFT** + **F10**|
|Menüler|Kısayol tuşlarını kullanarak bir menü öğesine hızlıca erişin. Komutu etkinleştirmek için **alt** tuşunu ve ardından bir menüdeki altı çizili harfleri seçin. örneğin, Visual Studio açık Project iletişim kutusunu görüntülemek için **Alt** + **F** + **O** + **P**' yi seçin.  <br><br> **Note:** standart Windows klavye kısayolu|**Alt**  +  **[harf]**|
|Arama kutusu|Visual Studio arama özelliğini kullanın.|**CTRL** + **Soru-cevap**|
|Araç kutusu penceresi|Araç kutusu sekmeleri arasında hareket edin.|**CTRL** + **Yukarı ok**<br /><br /> ve<br /><br /> **CTRL** + **Aşağı ok**|
|Araç kutusu penceresi|Araç kutusundan bir form veya tasarımcıya denetim ekleyin.|**Enter**|
|Seçenekler iletişim kutusu: ortam > klavye|**Kısayol tuşlarına basın** seçeneğinde girilen bir tuş birleşimini silin.|**Geri Al tuşu**|
|Bildirimler araç penceresi|İki klavye kısayol tuşu birleşimini ve diğeri tarafından izlenen bildirimler araç penceresini açın. Ardından, ok tuşlarını kullanarak bir bildirimi seçerek bunu seçin.| **CTRL** + **&#92;**, **CTRL** + **N**|

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Klavye kısayollarını kullanarak bildirimlere erişin

IDE 'de bir bildirim göründüğünde, bu, klavye kısayollarını kullanarak bildirimler penceresine nasıl erişekullanabileceğinizi aşağıda verilmiştir:

1. IDE 'nin herhangi bir yerinden, sırayla aşağıdaki iki klavye kısayoluna basın: **CTRL** + **&#92;** ve ardından **CTRL** + **N**.

   **Bildirimler** penceresi açılır.

   ![Visual Studio ıde 'de bildirimler araç penceresi](media/toast-notification.png "Visual Studio ıde 'de bildirimler penceresinin ekran görüntüsü")

1. Bir bildirim seçmek için **sekme** tuşunu ya da ok tuşlarını kullanın.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Derleme ve kesme noktası ipuçlarını ayarlamak için ses uygulamasını kullanın

Visual Studio program olaylarına bir ses atamak için Windows ses uygulamasını kullanabilirsiniz. Özellikle, aşağıdaki program olaylarına sesler atayabilirsiniz:

* Kesme noktası isabeti
* Derleme iptal edildi
* Oluşturma başarısız oldu
* Derleme başarılı oldu

Aşağıdaki adımları uygulayın:

1. Windows 10 çalıştıran bir bilgisayardaki **arama** kutusunda, **sistem seslerini değiştir** yazın.

   ![Windows 10 arama kutusu](media/type-here-to-search.png "Windows 10 arama kutusunun ekran görüntüsü")

   (alternatif olarak, Cortana etkinse, "Hey Cortana" deyin ve "sistem seslerini değiştirme" deyin.

1. **Sistem seslerini Değiştir**' e çift tıklayın.

   ![Windows 10 arama sonuçları](media/change-system-sounds.png "' Sistem seslerini Değiştir ' arama sonuçlarının Windows 10 ekran görüntüsü")

1. **Ses** iletişim kutusunda, **sesler** sekmesine tıklayın.

1. **Program olayları**' nda, **Microsoft Visual Studio**' ye kaydırın ve seçtiğiniz olaylara uygulamak istediğiniz sesleri seçin.

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
