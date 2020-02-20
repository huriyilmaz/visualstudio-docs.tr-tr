---
title: Visual Studio 2015 açıklamalı alt yazılar verilere bağlı denetimler için nasıl oluşturduğunu özelleştirme | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476912"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğeleri [veri kaynakları penceresinden](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) Windows Form Tasarımcısı sürüklediğinizde, yürütmeye özel bir değer verilir: başlık etiketlerindeki sütun adları, iki veya daha fazla sözcük birlikte art arda kaydırıldığında daha okunabilir bir dizeye yeniden biçimlendirilir. **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\10.0\Data tasarımcıları** kayıt defteri anahtarındaki **SmartCaptionExpression**, **Smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.

> [!NOTE]
> Oluşturduğunuz kadar bu kayıt defteri anahtarı mevcut değil.

 Akıllı resim yazısı, **SmartCaptionExpression** değerinin değerine girilen normal ifade tarafından denetlenir. **Veri tasarımcıları** kayıt defteri anahtarı eklendiğinde, Başlık etiketlerini denetleyen varsayılan normal ifade geçersiz kılınır. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Aşağıdaki tabloda başlık etiketindeki denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**Smartcaptionifadesi**|Normal ifade desenleri, eşleştirmek için kullanılır.|
|**Smartcaptiondeğiştirme**|**SmartCaptionExpression**ile eşleşen grupları görüntüleme biçimi.|
|**SmartCaptionSuffix**|Açıklamalı alt yazı sonuna eklenecek isteğe bağlı dize.|

 Bu kayıt defteri değerleri için iç varsayılan ayarları aşağıdaki tabloda listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**Smartcaptionifadesi**|(\\\p{Ll}) (\\\p{Lu}) &#124;_+|Ardından bir büyük harf veya alt çizgi, küçük harfli bir karakterle eşleşir.|
|**Smartcaptiondeğiştirme**|$1 $2|$1 ifadenin ilk parantez içinde eşleşen herhangi bir karakter ve $2 ikinci parantez içinde eşleşen herhangi bir karakteri temsil eder. Değişiklik, ilk eşleşme, boşluk ve ikinci Eşleştir ' dir.|
|**SmartCaptionSuffix**|:|Döndürülen dize için eklenmiş bir karakteri temsil eder. Örneğin, başlık `Company Name`ise, sonek bunu yapar `Company Name:`|

> [!CAUTION]
> Kayıt Defteri Düzenleyicisi'nde her şeyi yaparken çok dikkatli olmanız gerekir. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Microsoft Kayıt Defteri Düzenleyicisi'ni kullanarak neden sorunları çözülebilir garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresi akıllı açıklamalı alt yazı davranışını değiştirmek için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionExpression`adlı yeni bir **dize değeri** oluşturun.

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionReplacement`adlı yeni bir **dize değeri** oluşturun.

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionSuffix`adlı yeni bir **dize değeri** oluşturun.

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. **Veri kaynakları** penceresinin kullanmasını istediğiniz normal ifadeyi girin.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. Değiştirme girin, normal ifade ile eşleşen desenlerini görüntülemek istediğiniz şekilde biçimlendirilmiş bir dize.

15. **SmartCaptionSuffix** öğesine sağ tıklayın ve **Değiştir**' i seçin.

16. Açıklamalı alt yazı sonunda görünmesini istediğiniz herhangi bir karakter girin.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, başlık etiketleri, belirtilen yeni kayıt defteri değerleri kullanılarak oluşturulur.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Akıllı açıklamalı alt yazı özelliği devre dışı bırakmak için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve `Data Designers`adlı yeni bir **anahtar** oluşturun.

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionExpression`adlı yeni bir **dize değeri** oluşturun.

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionReplacement`adlı yeni bir **dize değeri** oluşturun.

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionSuffix`adlı yeni bir **dize değeri** oluşturun.

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. Değer için `(.*)` girin. Bu, tüm dizeyi eşleştirir.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. Değer için `$1` girin. Bu dizenin değişmeden kalır, böylece tüm dize olan eşleşen değerle değiştirir.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, resim yazısı etiketleri değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
