---
title: Veri bağlantılı denetimler için açıklamalı alt yazıları özelleştirme
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7780cfb3b266de6f477e74d1b352cf6b24aab42
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113666"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme

Öğeleri [veri kaynakları penceresinden](add-new-data-sources.md#data-sources-window) bir tasarımcıya sürüklediğinizde, yürütmeye özel bir göz önünde bulundurun: başlık etiketlerindeki sütun adları, iki veya daha fazla sözcük birlikte art arda kaydırıldığında daha okunabilir bir dizeye yeniden biçimlendirilir.

::: moniker range="vs-2017"

**HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\15.0\Data tasarımcıları** kayıt defteri anahtarındaki **SmartCaptionExpression**, **Smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\16.0\Data tasarımcıları** kayıt defteri anahtarındaki **SmartCaptionExpression**, **Smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.

::: moniker-end

> [!NOTE]
> Oluşturduğunuz kadar bu kayıt defteri anahtarı mevcut değil.

Akıllı Açıklamalı Altyazı değerini girilen normal ifade tarafından denetlenir **SmartCaptionExpression** değeri. Ekleme **veri tasarımcıları** kayıt defteri anahtarı başlık etiketindeki denetleyen varsayılan normal ifade geçersiz kılar. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

Aşağıdaki tabloda başlık etiketindeki denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**SmartCaptionExpression**|Desenlerinizi eşleştirmek için kullandığınız normal ifade.|
|**SmartCaptionReplacement**|İçinde eşleşen herhangi bir gruba görüntülenecek biçimi **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Açıklamalı alt yazı sonuna eklenecek isteğe bağlı dize.|

Bu kayıt defteri değerleri için iç varsayılan ayarları aşağıdaki tabloda listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll}) (\\\p{Lu}) &#124;_+**|Ardından bir büyük harf veya alt çizgi, küçük harfli bir karakterle eşleşir.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** , ifadenin ilk parantezleri ile eşleşen tüm karakterleri temsil eder ve **$2** ikinci parantez içinde eşleşen tüm karakterleri temsil eder. Değişiklik, ilk eşleşme, boşluk ve ikinci Eşleştir ' dir.|
|**SmartCaptionSuffix**|**:**|Döndürülen dize için eklenmiş bir karakteri temsil eder. Örneğin, açıklamalı alt yazı ise `Company Name`, sonek kolaylaştırır `Company Name:`|

> [!CAUTION]
> Kayıt defteri düzenleyicisinde herhangi bir şey yaparken çok dikkatli olun. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Microsoft Kayıt Defteri Düzenleyicisi'ni kullanarak neden sorunları çözülebilir garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
> Kayıt defterini yedekleme, düzenlemesi ve geri yükleme hakkında bilgi için bkz. [Gelişmiş kullanıcılar Için Windows kayıt defteri bilgileri](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirme

1. Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2. Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3. **HKEY_CURRENT_USER** > **yazılım** > **Microsoft** > **VisualStudio** düğümünü genişletin.

::: moniker range="vs-2017"

4. **15,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

::: moniker-end

5. **Veri tasarımcıları** düğümüne sağ tıklayın ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **SmartCaptionExpression** değerine sağ tıklayın ve **Değiştir**' i seçin.

7. İstediğiniz normal ifade girin **veri kaynakları** penceresini kullanın.

8. **Smartcaptiondeğiştirme** değerine sağ tıklayın ve **Değiştir**' i seçin.

9. Değiştirme girin, normal ifade ile eşleşen desenlerini görüntülemek istediğiniz şekilde biçimlendirilmiş bir dize.

10. **SmartCaptionSuffix** değerine sağ tıklayın ve **Değiştir**' i seçin.

11. Açıklamalı alt yazı sonunda görünmesini istediğiniz herhangi bir karakter girin.

    Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki sağlanan yeni kayıt defteri değerleri kullanılarak oluşturulur.

## <a name="turn-off-the-smart-captioning-feature"></a>Akıllı resim yazısı özelliğini kapatma

1. Bir komut penceresi açın **Başlat** ardından **çalıştırma**.

2. Tür `regedit` içinde **çalıştırma** iletişim kutusu seçeneğine tıklayıp **Tamam**.

3. **HKEY_CURRENT_USER** > **yazılım** > **Microsoft** > **VisualStudio** düğümünü genişletin.

::: moniker range="vs-2017"

4. **15,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

::: moniker-end

::: moniker range=">=vs-2019"

4. **16,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

::: moniker-end

5. **Veri tasarımcıları** düğümüne sağ tıklayın ve üç yeni dize değeri oluşturun:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Sağ **SmartCaptionExpression** öğesi ekleyin ve seçin **Değiştir**.

7. Girin `(.*)` değeri. Bu, tüm dizeyi eşleştirir.

8. Sağ **SmartCaptionReplacement** öğesi ekleyin ve seçin **Değiştir**.

9. Girin `$1` değeri. Bu dizenin değişmeden kalır, böylece tüm dize olan eşleşen değerle değiştirir.

    Sonraki öğeleri sürükleyin **veri kaynakları** penceresinde başlık etiketindeki değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
