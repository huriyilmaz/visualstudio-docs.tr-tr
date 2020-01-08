---
title: Hata ayıklama sırasında bir XPath ifadesini değerlendir
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e0b6c84fa9447dc38aa7976fa59bb5aa67d5c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592730"
---
# <a name="evaluate-xpath-expressions"></a>XPath ifadelerini değerlendir

Hata ayıklama sırasında **hızlı izleme** penceresini kullanarak XPath ifadelerini değerlendirebilirsiniz. XPath ifadesi W3C XPath 1,0 önerisine göre geçerli olmalıdır. Geçerli XSLT bağlamı (diğer bir deyişle, **Yereller** penceresindeki `self::node()` düğümü) XPath ifadesi için değerlendirme bağlamını sağlar.

Bir XPath ifadesi değerlendirilirken:

- Yerleşik XPath işlevleri desteklenir.

- Yerleşik XSLT işlevleri ve Kullanıcı tanımlı işlevler desteklenmez.

> [!NOTE]
> XSLT hata ayıklaması yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="evaluate-an-xpath-expression"></a>XPath ifadesini değerlendirme

Aşağıdaki yordam [Izlenecek yol: XSLT stil sayfası hata ayıklaması](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) sayfasında *below-Average. xsl* ve *Books. xml* dosyalarını kullanır.

1. `xsl:if` başlangıç etiketine bir kesme noktası ekleyin.

2. Hata ayıklamayı başlatmak için, menü çubuğunda **XSLT hata ayıklamayı Başlat** ' a > **XML** ' yi seçin (veya **alt**+**F5**tuşuna basın).

   Hata ayıklayıcı başlatılır ve `xsl:if` etiketinde kesilir.

3. Sağ tıklayın ve **hızlı gözcü**' ı seçin.

   **QuickWatch** penceresi açılır.

4. **QuickWatch** Iletişim kutusunun **ifade** alanına `./price/text()` girin ve sonra yeniden değerlendir ' **i seçin.**

   Geçerli kitap düğümünün fiyatı **değer** kutusunda görünür.

   ![Hızlı Gözcü penceresinde bir XPath ifadesini değerlendirme](media/quickwatch-price.png)

5. XPath ifadesini `./price/text() < $bookAverage` olarak değiştirin ve yeniden değerlendir **' e**tıklayın.

   **Değer** kutusunda XPath ifadesinin `true`olarak değerlendirildiği gösterilmektedir.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
