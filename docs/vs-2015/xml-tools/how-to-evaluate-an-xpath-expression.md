---
title: 'Nasıl yapılır: XPath Ifadesini değerlendirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670863"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Nasıl Yapılır: Bir XPath İfadesini Değerlendirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha **hızlı izleme** Iletişim kutusuyla XPath ifadelerini değerlendirebilirsiniz. XPath ifadesi W3C XPath 1,0 önerisine göre geçerli olmalıdır. Geçerli XSLT bağlamı — diğer bir deyişle, `self::node()` **Yereller** penceresindeki düğüm — XPath ifadesi için değerlendirme bağlamını sağlar.

 Aşağıdaki listede bir XPath ifadesi hesaplanırken hangi işlevlerin desteklendiği açıklanmaktadır:

- Yerleşik XPath işlevleri desteklenir.

- Yerleşik XSLT işlevleri desteklenmez.

- Kullanıcı tanımlı işlevler desteklenmez.

> [!NOTE]
> Aşağıdaki yordam, [Izlenecek yol: XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) konusunun belowAvg. xsl ve books.xml dosyalarını kullanır.

### <a name="to-evaluate-an-xpath-expression"></a>Bir XPath ifadesini değerlendirmek için

1. Başlangıç etiketine bir kesme noktası ekleyin `xsl:if` .

2. XML Düzenleyicisi araç çubuğundaki **XSL hata ayıkla** düğmesine tıklayın.

     Hata ayıklayıcı başlar ve `xsl:if` etiketi keser.

3. Sağ tıklayın ve **hızlı gözcü**' ı seçin.

     **QuickWatch** iletişim kutusu görüntülenir.

4. `./price/text()` **QuickWatch** iletişim kutusunun **ifade** alanına girip yeniden değerlendir ' e tıklayın. **Reevaluate**

     Geçerli kitap düğümünün fiyatı **değer** kutusunda görünür.

5. XPath ifadesini olarak değiştirin `./price/text() < $bookAverage` ve yeniden değerlendir **Reevaluate**' e tıklayın.

     **Değer** kutusunda XPath ifadesinin değerlendirme gösterilmektedir `true` .

## <a name="see-also"></a>Ayrıca Bkz.
 [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
