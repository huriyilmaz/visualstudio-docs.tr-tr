---
title: Veriye bağlı denetimler için açıklamalı alt yazıları özelleştirme
description: Veri Visual Studio denetimler için açıklamalı alt yazıların nasıl oluşturduğunı özelleştirin. Veri Kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirme. Akıllı açıklamalı alt yazıyı kapatın.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3a5979fda1e2fcbe8664df7171b1053acebb0506
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631443"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme

Öğeleri Veri Kaynakları [](add-new-data-sources.md#data-sources-window) penceresinden tasarımcıya sürüklerken dikkate alınması gereken önemli noktalar vardır: açıklamalı alt yazı etiketlerinin sütun adları, iki veya daha fazla sözcük bir araya geldiğinde daha okunabilir bir dizeye yeniden biçimlendirilebilir.

::: moniker range="vs-2017"

Kayıt defteri anahtarında **SmartCaptionExpression**, **SmartCaptionReplacement** ve **SmartCaptionSuffix** değerlerini **ayarerek bu etiketlerin oluşturulmaHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** özelleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Kayıt defteri anahtarında **SmartCaptionExpression**, **SmartCaptionReplacement** ve **SmartCaptionSuffix** değerlerini **ayarerek bu etiketlerin oluşturulmaHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designers** özelleştirebilirsiniz.

::: moniker-end

> [!NOTE]
> Bu kayıt defteri anahtarı siz oluşturmadan mevcut değildir.

Akıllı açıklamalı alt yazı, **SmartCaptionExpression** değerinin değerine girilen normal ifade tarafından denetlenr. Veri Tasarımcıları **kayıt defteri anahtarını eklemek,** açıklamalı alt yazı etiketlerini kontrol eden varsayılan normal ifadeyi geçersiz kılar. Normal ifadeler hakkında daha fazla bilgi için, [bkz. Using regular expressions in Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md).

Aşağıdaki tabloda açıklamalı alt yazı etiketlerini kontrol eden kayıt defteri değerleri açık almaktadır.

|Kayıt defteri öğesi|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|Desenlerinize uygun olarak kullanabileceğiniz normal ifade.|
|**SmartCaptionReplacement**|**SmartCaptionExpression** içinde eşlene tüm grupları görüntüleme biçimi.|
|**SmartCaptionSuffix**|Açıklamalı alt yazının sonuna eklenecek isteğe bağlı bir dize.|

Aşağıdaki tabloda, bu kayıt defteri değerleri için iç varsayılan ayarlar listele.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{Ll})( \\ \p{Lu})&#124;_+**|Ardından büyük harf veya alt çizgi gelen bir küçük harf karakteriyle eşler.|
|**SmartCaptionReplacement**|**1 ABD doları 2 ABD doları**|**$1,** ifadenin ilk parantezlerinde eş değere sahip tüm karakterleri temsil eder ve **$2, ikinci** parantezde eş değer olan karakterleri temsil eder. Değiştirme ilk eşleşme, boşluk ve ardından ikinci eşleşmedir.|
|**SmartCaptionSuffix**|**:**|Döndürülen dizeye eklenen bir karakteri temsil eder. Örneğin, açıklamalı alt yazı `Company Name` ise soneki bunu yapar `Company Name:`|

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi'nde herhangi bir şey yaparken çok dikkatli olun. Düzenlemeden önce kayıt defterini geri yükleme. Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sisteminizi yeniden yüklemenizi gerektirabilecek ciddi sorunlara neden olabilir. Microsoft, Kayıt Defteri Düzenleyicisi'ni kullanarak neden olduğunuz sorunların yanlış çözülebilir olduğunu garanti değildir. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
> Kayıt defterini yedekleme, düzenleme ve geri yükleme hakkında bilgi için bkz. [Windows için kayıt defteri bilgilerini yükleme.](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri Kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirme

1. Başlat'a ve ardından Çalıştır'a **tıklayarak** bir komut **penceresi açın.**

2. Çalıştır `regedit` iletişim kutusunu **yazın** ve Tamam'a **tıklayın.**

3. HKEY_CURRENT_USER   >    >  **Microsoft**  >  **VisualStudio düğümünü** genişletin.

::: moniker range="vs-2017"

4. **15.0 düğümüne sağ** tıklayın ve adlı yeni bir **Anahtar** `Data Designers` oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16.0 düğümüne sağ** tıklayın ve adlı yeni bir **Anahtar** `Data Designers` oluşturun.

::: moniker-end

5. Veri Tasarımcıları **düğümüne sağ tıklayın** ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **SmartCaptionExpression değerine sağ tıklayın ve** Değiştir'i **seçin.**

7. Veri Kaynakları penceresinin **kullanmalarını istediğiniz normal** ifadeyi girin.

8. **SmartCaptionReplacement değerine sağ tıklayın ve** Değiştir'i **seçin.**

9. Normal ifadenizin desenlerini görüntülemek istediğiniz şekilde biçimlendirilen değiştirme dizesini girin.

10. **SmartCaptionSuffix değerine sağ tıklayın ve** Değiştir'i **seçin.**

11. Açıklamalı alt yazının sonunda görünmesini istediğiniz karakterleri girin.

    Veri Kaynakları penceresinden öğeleri bir sonraki **sürükleyseniz,** açıklamalı alt yazı etiketleri sağlanan yeni kayıt defteri değerleri kullanılarak oluşturulur.

## <a name="turn-off-the-smart-captioning-feature"></a>Akıllı açıklamalı alt yazı özelliğini kapatma

1. Başlat'a ve ardından Çalıştır'a **tıklayarak** bir komut **penceresi açın.**

2. Çalıştır `regedit` iletişim kutusunu **yazın** ve Tamam'a **tıklayın.**

3. HKEY_CURRENT_USER   >    >  **Microsoft**  >  **VisualStudio düğümünü** genişletin.

::: moniker range="vs-2017"

4. **15.0 düğümüne sağ** tıklayın ve adlı yeni bir **Anahtar** `Data Designers` oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16.0 düğümüne sağ** tıklayın ve adlı yeni bir **Anahtar** `Data Designers` oluşturun.

::: moniker-end

5. Veri Tasarımcıları **düğümüne sağ tıklayın** ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **SmartCaptionExpression öğesini sağ tıklatın ve** Değiştir'i **seçin.**

7. Değeri `(.*)` olarak girin. Bu, dizenin tamamı ile eştir.

8. **SmartCaptionReplacement öğesini sağ tıklatın ve** Değiştir'i **seçin.**

9. Değeri `$1` olarak girin. Bu, dizeyi, değişmeden kalacak şekilde dizenin tamamı olan eş değerle değiştirir.

    Veri Kaynakları penceresinden öğeleri bir sonraki **sürükleyseniz,** açıklamalı alt yazı etiketleri değiştirilmemiş açıklamalı alt yazılarla oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
