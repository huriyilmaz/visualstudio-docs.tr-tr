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
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476912"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğeleri [veri kaynakları penceresinden](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) Windows Form Tasarımcısı sürüklediğinizde, yürütmeye özel bir değer verilir: başlık etiketlerindeki sütun adları, iki veya daha fazla sözcük birlikte art arda kaydırıldığında daha okunabilir bir dizeye yeniden biçimlendirilir. **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\10.0\Data tasarımcıları** kayıt defteri anahtarındaki **SmartCaptionExpression**, **Smartcaptiondeğişim**ve **SmartCaptionSuffix** değerlerini ayarlayarak bu etiketlerin oluşturulma biçimini özelleştirebilirsiniz.

> [!NOTE]
> Bu kayıt defteri anahtarı siz oluşturana kadar yok.

 Akıllı resim yazısı, **SmartCaptionExpression** değerinin değerine girilen normal ifade tarafından denetlenir. **Veri tasarımcıları** kayıt defteri anahtarı eklendiğinde, Başlık etiketlerini denetleyen varsayılan normal ifade geçersiz kılınır. Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Aşağıdaki tabloda, Başlık etiketlerini denetleyen kayıt defteri değerleri açıklanmaktadır.

|Kayıt defteri öğesi|Description|
|-------------------|-----------------|
|**Smartcaptionifadesi**|Desenlerinizi eşleştirmek için kullanılan normal ifade.|
|**Smartcaptiondeğiştirme**|**SmartCaptionExpression**ile eşleşen grupları görüntüleme biçimi.|
|**SmartCaptionSuffix**|Açıklamalı alt yazısının sonuna eklenecek isteğe bağlı bir dize.|

 Aşağıdaki tabloda, bu kayıt defteri değerleri için iç varsayılan ayarlar listelenmektedir.

|Kayıt defteri öğesi|Varsayılan değer|Açıklama|
|-------------------|-------------------|-----------------|
|**Smartcaptionifadesi**|( \\ \p{ll}) ( \\ \p{lu}) &#124;_ +|Küçük bir karakterle ve ardından büyük bir karakter veya alt çizgi ile eşleşir.|
|**Smartcaptiondeğiştirme**|$1 $2|$1, ifadenin ilk parantezleri ile eşleşen tüm karakterleri temsil eder ve $2 ikinci parantez içinde eşleşen tüm karakterleri temsil eder. Değiştirme ilk eşleşme, bir boşluk ve ikinci eşleşmedir.|
|**SmartCaptionSuffix**|:|Döndürülen dizeye eklenen bir karakteri temsil eder. Örneğin, resim yazısı ise `Company Name` , sonek bunu yapar `Company Name:`|

> [!CAUTION]
> Kayıt defteri düzenleyicisinde herhangi bir şey yaparken dikkatli olmanız gerekir. Düzenlemeden önce kayıt defterini yedekleyin. Kayıt Defteri Düzenleyicisi 'Ni yanlış kullanırsanız, işletim sisteminizi yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilirsiniz. Microsoft, kayıt defteri düzenleyicisini yanlış kullanarak neden olan sorunların çözümlenemeyeceğini garanti etmez. Kayıt Defteri Düzenleyicisi'ni kullanım riski size aittir.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Veri kaynakları penceresinin akıllı açıklamalı alt yazı davranışını değiştirmek için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. `regedit` **Çalıştır** iletişim kutusuna yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve adlı yeni bir **anahtar** oluşturun `Data Designers` .

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionExpression` .

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionReplacement` .

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionSuffix` .

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. **Veri kaynakları** penceresinin kullanmasını istediğiniz normal ifadeyi girin.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. Normal ifadenizde eşleşen desenleri göstermek istediğiniz şekilde biçimlendirilen değiştirme dizesini girin.

15. **SmartCaptionSuffix** öğesine sağ tıklayın ve **Değiştir**' i seçin.

16. Resim yazısının sonunda görünmesini istediğiniz karakterleri girin.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, başlık etiketleri, belirtilen yeni kayıt defteri değerleri kullanılarak oluşturulur.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Akıllı resim yazısı özelliğini kapatmak için

1. **Başlat** ' a ve ardından **Çalıştır**' a tıklayarak bir komut penceresi açın.

2. `regedit` **Çalıştır** iletişim kutusuna yazın ve **Tamam**' a tıklayın.

3. **HKEY_CURRENT_USER** düğümünü genişletin.

4. **Yazılım** düğümünü genişletin.

5. **Microsoft** düğümünü genişletin.

6. **VisualStudio** düğümünü genişletin.

7. **10,0** düğümüne sağ tıklayın ve adlı yeni bir **anahtar** oluşturun `Data Designers` .

8. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionExpression` .

9. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionReplacement` .

10. **Veri tasarımcıları** düğümüne sağ tıklayın ve adlı yeni bir **dize değeri** oluşturun `SmartCaptionSuffix` .

11. **SmartCaptionExpression** öğesine sağ tıklayın ve **Değiştir**' i seçin.

12. `(.*)`Değer için girin. Bu, tüm dizeyle eşleşir.

13. **Smartcaptiondeðiþtirme** öğesine sağ tıklayın ve **Değiştir**' i seçin.

14. `$1`Değer için girin. Bu, dizeyi, değiştirilmeden kalacak şekilde tüm dize olan eşleşen değerle değiştirir.

     Öğeleri **veri kaynakları** penceresinden bir dahaki sefer sürüklediğinizde, resim yazısı etiketleri değiştirilmemiş açıklamalı alt yazılar ile oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
