---
title: Hata ayıklama sırasında bir XPath ifadesini değerlendir
ms.date: 03/05/2019
description: Hata ayıklama sırasında hızlı Izleme penceresini kullanarak XPath ifadelerini değerlendirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068362f88d801d44a1a6b6a85c74f97ba2d3c773
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399747"
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

2. Hata ayıklamayı başlatmak için, **XML**  >  menü çubuğunda XML **XSLT hata ayıklamayı Başlat** ' ı seçin (veya **alt** + **F5** tuşuna basın).

   Hata ayıklayıcı başlar ve `xsl:if` etiketi keser.

3. Sağ tıklayın ve **hızlı gözcü** ' ı seçin.

   **QuickWatch** penceresi açılır.

4. `./price/text()` **QuickWatch** iletişim kutusunun **ifade** alanına girip yeniden değerlendir ' i seçin. **Reevaluate**

   Geçerli kitap düğümünün fiyatı **değer** kutusunda görünür.

   ![Hızlı Gözcü penceresinde bir XPath ifadesini değerlendirme](media/quickwatch-price.png)

5. XPath ifadesini olarak değiştirin `./price/text() < $bookAverage` ve yeniden değerlendir **Reevaluate** ' e tıklayın.

   **Değer** kutusunda XPath ifadesinin değerlendirme gösterilmektedir `true` .

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
