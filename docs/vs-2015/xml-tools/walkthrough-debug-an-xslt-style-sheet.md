---
title: 'İzlenecek yol: XSLT stil sayfasında hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c205ff68ebc51d0b0f5b32038763c1741855d7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656115"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İzlenecek Yol: XSLT Stil Sayfasında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda bulunan adımlarda XSLT hata ayıklamanın nasıl kullanılacağı gösterilmektedir. Adımlar, değişkenleri görüntüleme, kesme noktalarını ayarlama ve kodun üzerinden atlama içerir. Stil sayfası, ortalama defter fiyatının altında maliyeti olan tüm kitapları bulur.

### <a name="to-prepare-for-this-walkthrough"></a>Bu adım adım izleme için hazırlanmak amacıyla

1. Açık olan tüm çözümleri kapatın.

2. İki örnek dosyayı yerel bilgisayarınıza kopyalayın.

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

#### <a name="to-start-debugging"></a>Hata ayıklamayı başlatmak için

1. **Dosya** menüsünde **Aç**' ın üzerine gelin ve **Dosya**' ya tıklayın.

2. BelowAvg. xsl dosyasını bulun ve **Aç**' a tıklayın.

    Stil sayfası XML düzenleyicisinde açılır.

3. Belge Özellikleri penceresinin **giriş** alanındaki gezinme düğmesine ( **...** ) tıklayın.

4. Books. xml dosyasını bulun ve **Aç**' a tıklayın.

    Bu, XSLT dönüştürmesi için kullanılan kaynak belge dosyasını ayarlar.

5. @No__t_0 başlangıç etiketine sağ tıklayın, **kesme**noktası ' nın üzerine gelin ve **kesme noktası Ekle**' ye tıklayın.

6. XML Düzenleyicisi araç çubuğundaki **XSL hata ayıkla** düğmesine tıklayın.

   Böylece hata ayıklama işlemi başlatılır ve hata ayıklayıcı tarafından kullanılan birkaç yeni pencere açılır.

   Giriş belgesi ve stilleri sayfasını görüntüleyen iki pencere vardır. Hata ayıklayıcı, geçerli yürütme durumunu göstermek için bu pencereleri kullanır. Hata ayıklayıcı, stil sayfasının `xsl:if` öğesinde ve Books. xml dosyasındaki ilk kitap düğümünde konumlandırılır.

   Yereller penceresi tüm yerel değişkenleri ve bunların geçerli değerlerini görüntüler. Bu, stil sayfasında tanımlanan değişkenleri ve ayrıca hata ayıklayıcının Şu anda bağlamdaki düğümleri izlemek için kullandığı değişkenleri içerir.

   **XSL çıkış** PENCERESI, XSL dönüşümünün çıkışını görüntüler. Bu pencere, **Visual Studio çıktı** penceresinden ayrıdır.

## <a name="watch-window"></a>Gözcü penceresi

#### <a name="to-use-the-watch-window"></a>izleme penceresi kullanmak için

1. **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin, **İzle**' ye gelin ve **1. izle**' ye tıklayın.

     Bu, Gözcü 1 penceresini görünür hale getirir.

2. **Ad** alanına `$bookAverage` YAZıN ve ENTER tuşuna basın.

     @No__t_0 değişkenin değeri pencerede görüntülenir.

3. **Ad** alanına `self::node()` YAZıN ve ENTER tuşuna basın.

     `self::node()`, geçerli bağlam düğümünü değerlendiren bir XPath ifadesidir. @No__t_0 XPath ifadesinin değeri ilk kitap düğümüdür. Bu, dönüşümde ilerlemede olduğu gibi değişir.

4. @No__t_0 düğümünü genişletin ve `price` düğümünü genişletin.

     Bu, kitap fiyatının değerini görmenizi sağlar ve `$bookAverage` değeriyle kolayca karşılaştırabilirsiniz. Kitap fiyatı ortalamanın altında olduğundan `xsl:if` koşulu başarılı olmalıdır.

## <a name="step-through-the-code"></a>Kod Içinde adımla
 Hata ayıklayıcı, kodu tek seferde bir satır yürütmenize olanak sağlar.

#### <a name="to-step-through-the-code"></a>Kod boyunca ilerlemek için

1. Devam etmek için **F5** 'e basın.

     İlk kitap düğümü `xsl:if` koşulunu karşıladığı için kitap düğümü, XSL çıkış penceresine eklenir. Hata ayıklayıcı, stil sayfasındaki `xsl:if` öğesinde yeniden konumlandırılana kadar yürütülmeye devam eder. Hata ayıklayıcı artık Books. xml dosyasındaki ikinci kitap düğümüne yerleştirildi.

     Watch1 penceresinde `self::node()` değeri ikinci kitap düğümüne değişir. Price öğesinin değerini inceleyerek, fiyatın ortalamanın üzerinde olduğunu belirleyebilir, bu nedenle `xsl:if` koşulu başarısız olmalıdır.

2. Devam etmek için **F5** 'e basın.

     İkinci kitap düğümü `xsl:if` koşulunu karşılamadığından, kitap düğümü XSL çıkış penceresine eklenmez. Hata ayıklayıcı, stil sayfasındaki `xsl:if` öğesinde yeniden konumlandırılana kadar yürütülmeye devam eder. Hata ayıklayıcı artık Books. xml dosyasındaki üçüncü `book` düğümüne konumlandırıldı.

     Watch1 penceresinde `self::node()` değeri üçüncü kitap düğümüne dönüşür. @No__t_0 öğesinin değerini inceleyerek, fiyatın ortalamanın altında olduğunu belirleyebilir, bu nedenle `xsl:if` koşulunun başarılı olması gerekir.

3. Devam etmek için **F5** 'e basın.

     @No__t_0 koşul karşılandığından, üçüncü kitap XSL çıkış penceresine eklenir. XML belgesindeki tüm kitaplar işlendi ve hata ayıklayıcı durdu.

## <a name="sample-files"></a>Örnek dosyalar
 Aşağıdaki iki dosya izlenecek yol tarafından kullanılır.

### <a name="belowavgxsl"></a>belowAvg. Xsl

```
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books. xml

```
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
