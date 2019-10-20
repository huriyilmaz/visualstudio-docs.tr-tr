---
title: Visual Studio 2015 ' nin veri bağlantılı denetimler için nasıl resim yazısı oluşturduğunu özelleştirin | Microsoft Docs
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
ms.openlocfilehash: 04f32fa0426039f50c0a0352ef0b04900d705a98
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657437"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğeleri [veri kaynakları penceresinden](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) Windows Form Tasarımcısı sürüklediğinizde, yürütmeye özel bir değer verilir: başlık etiketlerindeki sütun adları, art arda iki veya daha fazla sözcük bulunduğunda daha okunabilir bir dizeye yeniden biçimlendirilir birbiriyle. HKEY_Current_User\Software\Microsoft\VisualStudio\ içinde **SmartCaptionExpression**, **smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.  **10.0 \ Veri tasarımcıları** kayıt defteri anahtarı.

> [!NOTE]
> Bu kayıt defteri anahtarı siz oluşturana kadar yok.

 Akıllı resim yazısı, **SmartCaptionExpression** değerinin değerine girilen normal ifade tarafından denetlenir. **Veri tasarımcıları** kayıt defteri anahtarı eklendiğinde, Başlık etiketlerini denetleyen varsayılan normal ifade geçersiz kılınır. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Aşağıdaki tabloda, Başlık etiketlerini denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Açıklama|
|-------------------|-----------------|
|**Smartcaptionifadesi**|Desenlerinizi eşleştirmek için kullanılan normal ifade.|
|**Smartcaptiondeğiştirme**|**SmartCaptionExpression**ile eşleşen grupları görüntüleme biçimi.|
|**SmartCaptionSuffix**|Açıklamalı alt yazısının sonuna eklenecek isteğe bağlı bir dize.|

 Aşağıdaki tabloda, bu kayıt defteri değerleri için iç varsayılan ayarlar listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**Smartcaptionifadesi**|(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+|Küçük bir karakterle ve ardından büyük bir karakter veya alt çizgi ile eşleşir.|
|**Smartcaptiondeğiştirme**|$1 $2|$1, ifadenin ilk parantezleri ile eşleşen tüm karakterleri temsil eder ve $2 ikinci parantez içinde eşleşen tüm karakterleri temsil eder. Değiştirme ilk eşleşme, bir boşluk ve ikinci eşleşmedir.|
|**SmartCaptionSuffix**|:|Döndürülen dizeye eklenen bir karakteri temsil eder. Örneğin, başlık `Company Name` ise, sonek bunu yapar `Company Name:`|

> [!CAUTION]
> Kayıt defteri düzenleyicisinde herhangi bir şey yaparken dikkatli olmanız gerekir. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sisteminizi yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Microsoft, kayıt defteri düzenleyicisini yanlış kullanarak neden olan sorunların çözümlenemeyeceğini garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.
>
> Aşağıdaki Bilgi Bankası makalesi, kayıt defterini yedekleme, düzenlemeyle ve geri yüklemeyle ilgili yönergeler içermektedir: [Microsoft Windows kayıt defteri açıklaması](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-US; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirmek için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionExpression` adlı yeni bir **dize değeri** oluşturun.

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionReplacement` adlı yeni bir **dize değeri** oluşturun.

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionSuffix` adlı yeni bir **dize değeri** oluşturun.

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. **Veri kaynakları** penceresinin kullanmasını istediğiniz normal ifadeyi girin.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. Normal ifadenizde eşleşen desenleri göstermek istediğiniz şekilde biçimlendirilen değiştirme dizesini girin.

15. **SmartCaptionSuffix** öğesine sağ tıklayın ve **Değiştir**' i seçin.

16. Resim yazısının sonunda görünmesini istediğiniz karakterleri girin.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, başlık etiketleri, belirtilen yeni kayıt defteri değerleri kullanılarak oluşturulur.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Akıllı resim yazısı özelliğini kapatmak için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. **Çalıştır** iletişim kutusuna `regedit` yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve `Data Designers` adlı yeni bir **anahtar** oluşturun.

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionExpression` adlı yeni bir **dize değeri** oluşturun.

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionReplacement` adlı yeni bir **dize değeri** oluşturun.

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve `SmartCaptionSuffix` adlı yeni bir **dize değeri** oluşturun.

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. Değer için `(.*)` girin. Bu, tüm dizeyle eşleşir.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. Değer için `$1` girin. Bu, dizeyi, değiştirilmeden kalacak şekilde tüm dize olan eşleşen değerle değiştirir.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, resim yazısı etiketleri değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
