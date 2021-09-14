---
title: Hata ayıklama sırasında bir XPath ifadesini değerlendir
ms.date: 03/05/2019
description: Hata ayıklama sırasında hızlı Izleme penceresini kullanarak XPath ifadelerini değerlendirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: a5d229bc035edcb3460ca57050ddfd1988d94587
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726038"
---
# <a name="evaluate-xpath-expressions"></a>XPath ifadelerini değerlendir

Hata ayıklama sırasında **hızlı izleme** penceresini kullanarak XPath ifadelerini değerlendirebilirsiniz. XPath ifadesi W3C XPath 1,0 önerisine göre geçerli olmalıdır. Geçerli XSLT bağlamı (diğer bir deyişle, `self::node()` **Yereller** penceresindeki düğüm) XPath ifadesi için değerlendirme bağlamını sağlar.

Bir XPath ifadesi değerlendirilirken:

- Yerleşik XPath işlevleri desteklenir.

- Yerleşik XSLT işlevleri ve Kullanıcı tanımlı işlevler desteklenmez.

> [!NOTE]
> XSLT hata ayıklaması yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="evaluate-an-xpath-expression"></a>XPath ifadesini değerlendirme

Aşağıdaki yordam [Izlenecek yol: XSLT stil sayfası hata ayıklaması](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) sayfasında *below-Average. xsl* ve *books.xml* dosyalarını kullanır.

1. Başlangıç etiketine bir kesme noktası ekleyin `xsl:if` .

2. Hata ayıklamayı başlatmak için,   >  menü çubuğunda XML **XSLT hata ayıklamayı Başlat** ' ı seçin (veya **alt** + **F5** tuşuna basın).

   Hata ayıklayıcı başlar ve `xsl:if` etiketi keser.

3. Sağ tıklayın ve **hızlı gözcü**' ı seçin.

   **QuickWatch** penceresi açılır.

4. `./price/text()` **QuickWatch** iletişim kutusunun **ifade** alanına girip yeniden değerlendir ' i seçin. 

   Geçerli kitap düğümünün fiyatı **değer** kutusunda görünür.

   ![Hızlı Gözcü penceresinde bir XPath ifadesini değerlendirme](media/quickwatch-price.png)

5. XPath ifadesini olarak değiştirin `./price/text() < $bookAverage` ve yeniden değerlendir ' e tıklayın.

   **Değer** kutusunda XPath ifadesinin değerlendirme gösterilmektedir `true` .

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
