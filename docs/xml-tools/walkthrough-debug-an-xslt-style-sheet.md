---
title: XSLT stil sayfalarında hata ayıkla
description: bu kılavuzda bulunan adımları izleyerek xslt stil sayfasında hata ayıklamak için Visual Studio xslt hata ayıklayıcısını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: b591b597b2cb0930c2ee2e3c4ceb23158ac2956c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025153"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İzlenecek yol: XSLT stil sayfasında hata ayıklama

Bu izlenecek yolda bulunan adımlarda XSLT hata ayıklamanın nasıl kullanılacağı gösterilmektedir. Adımlar, değişkenleri görüntüleme, kesme noktalarını ayarlama ve kodun üzerinden atlama içerir. Hata ayıklayıcı, kodu tek seferde yürütmenize olanak sağlar.

Bu izlenecek yol için hazırlanmak üzere, önce iki [örnek dosyayı](#sample-files) yerel bilgisayarınıza kopyalayın. Stil sayfası, diğeri ise stil sayfasına giriş olarak kullanacağımız XML dosyasıdır. Bu kılavuzda, kullandığımız stil sayfası maliyeti ortalama defter fiyatının altında olan tüm kitapları bulur.

> [!NOTE]
> XSLT hata ayıklayıcısı yalnızca Visual Studio Professional ve Enterprise sürümlerinde kullanılabilir.

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

1. **Dosya** menüsünden dosya **Aç**' ı seçin  >  .

2. *Below-Average. xsl* dosyasını bulun ve **Aç**' ı seçin.

   Stil sayfası XML düzenleyicisinde açılır.

3. Belge Özellikleri penceresinin **giriş** alanındaki gezinme düğmesine (**...**) tıklayın. ( **Özellikler** penceresi görünür değilse, düzenleyicide açık dosyada herhangi bir yere sağ tıklayın ve ardından **Özellikler**' i seçin.)

4. *books.xml* dosyasını bulun ve **Aç**' ı seçin.

   Bu, XSLT dönüştürmesi için kullanılan kaynak belge dosyasını ayarlar.

5. 12 *. satırda below-Average. xsl* üzerine bir [kesme noktası](../debugger/using-breakpoints.md) ayarlayın. Bunu birden çok şekilde yapabilirsiniz:

   - 12. satırda düzenleyicinin kenar boşluğuna tıklayın.

   - 12. satırda herhangi bir yere tıklayın ve ardından **F9** tuşuna basın.

   - Başlangıç etiketini sağ tıklatın `xsl:if` ve **kesme** noktası  >  **Ekle kesme noktası**' nı seçin.

      ![Visual Studio içindeki XSL dosyasında kesme noktası ekle](media/insert-breakpoint.PNG)

6. Menü çubuğunda, **XML**  >  **XSLT hata ayıklamayı Başlat** ' ı seçin (veya **alt** + **F5** tuşuna basın).

   Hata ayıklama işlemi başlar.

   Düzenleyicide, hata ayıklayıcı `xsl:if` stil sayfasının öğesine yerleştirilir. *below-average.xml* adlı başka bir dosya düzenleyicide açılır; Bu, giriş dosyasındaki her düğüm *books.xml* işlendiği şekilde doldurulacak çıkış dosyasıdır.

   **oto, yereller** ve  **gözcü 1** pencereleri Visual Studio penceresinin en altında görünür. **Yereller** penceresi tüm yerel değişkenleri ve bunların geçerli değerlerini görüntüler. Bu, stil sayfasında tanımlanan değişkenleri ve ayrıca hata ayıklayıcının Şu anda bağlamdaki düğümleri izlemek için kullandığı değişkenleri içerir.

## <a name="watch-window"></a>Gözcü penceresi

Giriş dosyası işlendiğinde değerlerini inceleyebileceğiniz için, **1. gözcü** penceresine iki değişken ekleyeceğiz. (İzlemek istediğiniz değişkenler zaten orada ise, değerleri incelemek için **Yereller** penceresini de kullanabilirsiniz.)

1. **hata ayıkla** menüsünden **Windows**  >  **izle**  >  **izle 1**' i seçin.

   **1. gözcü** penceresi görünür hale gelir.

2. `$bookAverage` **Ad** alanına yazın ve ardından **ENTER** tuşuna basın.

   `$bookAverage`Değişkenin değeri **değer** alanında görüntülenir.

3. Sonraki satırda, `self::node()` **ad** alanına yazın ve ardından **ENTER** tuşuna basın.

   `self::node()` , geçerli bağlam düğümünü değerlendiren bir XPath ifadesidir. `self::node()`XPath ifadesinin değeri ilk kitap düğümüdür. Bu, dönüşümde ilerlemede olduğu gibi değişir.

4. Düğümünü genişletin `self::node()` ve ardından değeri olan düğümü genişletin `price` .

   ![izleme penceresi XSLT hata ayıklaması sırasında Visual Studio](media/xslt-debugging-watch-window.png)

   Geçerli kitap düğümü için kitap fiyatının değerini görebilir ve değeri ile karşılaştırabilirsiniz `$bookAverage` . Kitap fiyatı ortalamanın altında olduğundan, `xsl:if` hata ayıklama işlemine devam ettiğinizde koşulun başarılı olması gerekir.

## <a name="step-through-the-code"></a>Kod içinde adımla

1. Devam etmek için **F5** 'e basın.

   İlk kitap düğümü koşulu karşıladığından `xsl:if` , kitap düğümü *below-average.xml* çıktı dosyasına eklenir. Hata ayıklayıcı, stil sayfasındaki öğe üzerinde yeniden konumlandırılana kadar yürütülmeye devam eder `xsl:if` . Hata ayıklayıcı artık *books.xml* dosyasındaki ikinci kitap düğümüne yerleştirildi.

   1. **Gözcü** penceresinde, `self::node()` değer ikinci kitap düğümüne değişir. Price öğesinin değerini inceleyerek, fiyatın ortalamanın üzerinde olduğunu ve bu nedenle `xsl:if` koşulun başarısız olması gerektiğini belirleyebilirsiniz.

2. Devam etmek için **F5** 'e basın.

   İkinci kitap düğümü `xsl:if` koşulu karşılamadığından, kitap düğümü *below-average.xml* çıkış dosyasına eklenmez. Hata ayıklayıcı, stil sayfasındaki öğe üzerinde yeniden konumlandırılana kadar yürütülmeye devam eder `xsl:if` . Hata ayıklayıcı artık `book` *books.xml* dosyasındaki üçüncü düğüme konumlandırılmış.

   1. **Gözcü** penceresinde, `self::node()` değer üçüncü kitap düğümüne değişir. Öğesinin değerini inceleyerek `price` , fiyatın ortalamanın altında olduğunu belirleyebilirsiniz. `xsl:if`Koşul başarılı olmalıdır.

3. Devam etmek için **F5** 'e basın.

   `xsl:if`Koşul karşılandığından, üçüncü kitap *below-average.xml* çıkış dosyasına eklenir. XML belgesindeki tüm kitaplar işlendi ve hata ayıklayıcı durdu.

## <a name="sample-files"></a>Örnek dosyalar

Aşağıdaki iki dosya izlenecek yol tarafından kullanılır.

### <a name="below-averagexsl"></a>Below-Average. Xsl

```xml
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
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
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

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
