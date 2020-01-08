---
title: XSLT stil sayfalarında hata ayıkla
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592483"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İzlenecek yol: XSLT stil sayfasında hata ayıklama

Bu izlenecek yolda bulunan adımlarda XSLT hata ayıklamanın nasıl kullanılacağı gösterilmektedir. Adımlar, değişkenleri görüntüleme, kesme noktalarını ayarlama ve kodun üzerinden atlama içerir. Hata ayıklayıcı, kodu tek seferde yürütmenize olanak sağlar.

Bu izlenecek yol için hazırlanmak üzere, önce iki [örnek dosyayı](#sample-files) yerel bilgisayarınıza kopyalayın. Stil sayfası, diğeri ise stil sayfasına giriş olarak kullanacağımız XML dosyasıdır. Bu kılavuzda, kullandığımız stil sayfası maliyeti ortalama defter fiyatının altında olan tüm kitapları bulur.

> [!NOTE]
> XSLT hata ayıklayıcısı yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="start-debugging"></a>Hata Ayıklamayı Başlat

1. **Dosya** menüsünden > **dosyayı** **Aç** ' ı seçin.

2. *Below-Average. xsl* dosyasını bulun ve **Aç**' ı seçin.

   Stil sayfası XML düzenleyicisinde açılır.

3. Belge Özellikleri penceresinin **giriş** alanındaki gezinme düğmesine ( **...** ) tıklayın. ( **Özellikler** penceresi görünür değilse, düzenleyicide açık dosyada herhangi bir yere sağ tıklayın ve ardından **Özellikler**' i seçin.)

4. *Books. xml* dosyasını bulun ve **Aç**' ı seçin.

   Bu, XSLT dönüştürmesi için kullanılan kaynak belge dosyasını ayarlar.

5. 12 *. satırda below-Average. xsl*üzerine bir [kesme noktası](../debugger/using-breakpoints.md) ayarlayın. Bunu birden çok şekilde yapabilirsiniz:

   - 12. satırda düzenleyicinin kenar boşluğuna tıklayın.

   - 12. satırda herhangi bir yere tıklayın ve ardından **F9**tuşuna basın.

   - `xsl:if` Başlangıç etiketini sağ tıklatın ve **ardından kesme noktası** **Ekle** > kesme noktası ' nı seçin.

      ![Visual Studio 'da XSL dosyasında kesme noktası ekle](media/insert-breakpoint.PNG)

6. Menü çubuğunda, **XML** > **XSLT hata ayıklamayı Başlat** ' ı seçin (veya **alt**+**F5**tuşuna basın).

   Hata ayıklama işlemi başlar.

   Düzenleyicide, hata ayıklayıcı stil sayfasının `xsl:if` öğesinde konumlandırılır. Düzenleyicide *below-Average. xml* adlı başka bir dosya açılır; Bu, giriş dosyası defterlerindeki her düğüm olarak doldurulacak çıkış dosyasıdır *. xml* işlenir.

   **Oto, Yereller**ve **Gözcü 1** pencereleri, Visual Studio penceresinin alt kısmında görünür. **Yereller** penceresi tüm yerel değişkenleri ve bunların geçerli değerlerini görüntüler. Bu, stil sayfasında tanımlanan değişkenleri ve ayrıca hata ayıklayıcının Şu anda bağlamdaki düğümleri izlemek için kullandığı değişkenleri içerir.

## <a name="watch-window"></a>İzleme penceresi

Giriş dosyası işlendiğinde değerlerini inceleyebileceğiniz için, **1. gözcü** penceresine iki değişken ekleyeceğiz. (İzlemek istediğiniz değişkenler zaten orada ise, değerleri incelemek için **Yereller** penceresini de kullanabilirsiniz.)

1. **Hata Ayıkla** menüsünde **Windows** > **İzle** ** > izle**' yi seçin.

   **1. gözcü** penceresi görünür hale gelir.

2. **Ad** alanına `$bookAverage` yazın ve ardından **ENTER**tuşuna basın.

   `$bookAverage` değişkenin değeri **değer** alanında görüntülenir.

3. Sonraki satırda, **ad** alanına `self::node()` yazın ve ardından **ENTER**tuşuna basın.

   `self::node()`, geçerli bağlam düğümünü değerlendiren bir XPath ifadesidir. `self::node()` XPath ifadesinin değeri ilk kitap düğümüdür. Bu, dönüşümde ilerlemede olduğu gibi değişir.

4. `self::node()` düğümünü genişletin ve ardından değeri `price`olan düğümü genişletin.

   ![Visual Studio 'da XSLT hata ayıklaması sırasında izleme penceresi](media/xslt-debugging-watch-window.png)

   Geçerli kitap düğümü için kitap fiyatının değerini görebilir ve `$bookAverage` değeriyle karşılaştırabilirsiniz. Kitap fiyatı ortalamanın altında olduğundan, hata ayıklama işlemine devam ettiğinizde `xsl:if` koşulun başarılı olması gerekir.

## <a name="step-through-the-code"></a>Kod içinde adımla

1. Devam etmek için **F5** tuşuna basın.

   İlk kitap düğümü `xsl:if` koşulunu karşıladığı için kitap düğümü *below-Average. xml* çıkış dosyasına eklenir. Hata ayıklayıcı, stil sayfasındaki `xsl:if` öğesinde yeniden konumlandırılana kadar yürütülmeye devam eder. Hata ayıklayıcı artık *Books. xml* dosyasındaki ikinci kitap düğümüne yerleştirildi.

   1\. **Gözcü** penceresinde, `self::node()` değeri ikinci kitap düğümüne değişir. Price öğesinin değerini inceleyerek, fiyatın ortalamanın üzerinde olduğunu belirleyebilir, bu nedenle `xsl:if` koşulu başarısız olmalıdır.

2. Devam etmek için **F5** tuşuna basın.

   İkinci kitap düğümü `xsl:if` koşulunu karşılamadığından, kitap düğümü *below-Average. xml* çıkış dosyasına eklenmez. Hata ayıklayıcı, stil sayfasındaki `xsl:if` öğesinde yeniden konumlandırılana kadar yürütülmeye devam eder. Hata ayıklayıcı artık *Books. xml* dosyasındaki üçüncü `book` düğümüne konumlandırıldı.

   1\. **Gözcü** penceresinde, `self::node()` değeri üçüncü kitap düğümüne dönüşür. `price` öğesinin değerini inceleyerek, fiyatın ortalamanın altında olduğunu belirleyebilirsiniz. `xsl:if` koşulu başarılı olmalıdır.

3. Devam etmek için **F5** tuşuna basın.

   `xsl:if` koşul karşılandığından, üçüncü kitap *below-Average. xml* çıkış dosyasına eklenir. XML belgesindeki tüm kitaplar işlendi ve hata ayıklayıcı durdu.

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

### <a name="booksxml"></a>Books. xml

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
