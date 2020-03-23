---
title: Hata Ayıklama XSLT stil sayfaları
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301722"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İziçin: XSLT stil sayfasını hata ayıklama

Bu izbisteki adımlar XSLT hata ayıklayıcısının nasıl kullanılacağını gösterir. Adımlar değişkenleri görüntülemeyi, kesme noktalarını ayarlamayı ve kodda adım atamayı içerir. Hata ayıklayıcı, kodu aynı anda bir satır yürütmenize olanak tanır.

Bu izbetmeye hazırlanmak için, önce iki [örnek dosyayı](#sample-files) yerel bilgisayarınıza kopyalayın. Biri stil sayfası, diğeri de stil sayfasına giriş olarak kullanacağımız XML dosyasıdır. Bu izbin de, kullandığımız stil sayfası, maliyeti ortalama kitap fiyatının altında olan tüm kitapları bulur.

> [!NOTE]
> XSLT hata ayıklayıcı yalnızca Visual Studio'nun Enterprise sürümünde kullanılabilir.

## <a name="start-debugging"></a>Hata ayıklama yı başlatma

1. **Dosya** menüsünden **Dosyaaç'ı** > **File**seçin.

2. *Ortalamanın altındaki.xsl* dosyasını bulun ve **Aç'ı**seçin.

   Stil sayfası XML düzenleyicisinde açılır.

3. Belge özellikleri penceresinin **Giriş** alanında gözat düğmesini (**...**) tıklatın. (Özellikler **Properties** penceresi görünmüyorsa, düzenleyicideki açık dosyanın herhangi bir yerine sağ tıklayın ve ardından **Özellikler'i**seçin.)

4. *books.xml* dosyasını bulun ve sonra **Aç'ı**seçin.

   Bu, XSLT dönüşümü için kullanılan kaynak belge dosyasını ayarlar.

5. *Ortalamanın 12.xsl altında*satırında bir [kesme noktası](../debugger/using-breakpoints.md) ayarlayın. Bunu birden çok şekilde yapabilirsiniz:

   - Satır 12'deki düzenleyicinin kenar boşluğuna tıklayın.

   - Satır 12'de herhangi bir yere tıklayın ve ardından **F9 tuşuna**basın.

   - Başlat etiketine `xsl:if` sağ tıklayın ve ardından **Kesme Noktası** > **Ekleme Noktası'nı**seçin.

      ![Visual Studio'da XSL dosyasına kesme noktası ekleme](media/insert-breakpoint.PNG)

6. Menü çubuğunda **XML** > **Start XSLT Hata Ayıklama'yı** seçin (veya **Alt**+**F5**tuşuna basın).

   Hata ayıklama işlemi başlar.

   Düzenleyicide hata ayıklama stil sayfasının `xsl:if` öğesine konumlandırılır. *Ortalama.xml'nin altında* adlı başka bir dosya editörde açılır; bu, giriş dosyası *kitaplarındaki* her düğüm işlenirken doldurulacak çıktı dosyasıdır.

   **Autos**, **Locals**ve **Watch 1** pencereleri Visual Studio penceresinin alt kısmında görünür. **Yereller** penceresi tüm yerel değişkenleri ve geçerli değerlerini görüntüler. Bu, stil sayfasında tanımlanan değişkenleri ve hata ayıklayanın şu anda bağlamiçinde olan düğümleri izlemek için kullandığı değişkenleri içerir.

## <a name="watch-window"></a>Gözcü penceresi

Giriş dosyası işlenirken değerlerini inceleyebilmemiz için **Watch 1** penceresine iki değişken ekleyeceğiz. (İzlemek istediğiniz değişkenler zaten varsa değerleri incelemek için **Yereller** penceresini de kullanabilirsiniz.)

1. Hata **Ayıklama** menüsünden **Windows** > **Watch** > **Watch 1'i**seçin.

   **Watch 1** penceresi görünür hale gelir.

2. Ad `$bookAverage` alanına **Name** yazın ve enter **tuşuna**basın.

   Değer alanındaki `$bookAverage` değişken ekranlarının **Value** değeri.

3. Bir sonraki `self::node()` satırda, **Ad** alanına yazın ve sonra **Enter**tuşuna basın.

   `self::node()`geçerli bağlam düğümüne değerlendiren bir XPath ifadesidir. `self::node()` XPath ifadesinin değeri ilk kitap düğümüdür. Dönüşüm boyunca ilerledikçe bu durum değişir.

4. Düğümü `self::node()` genişletin ve sonra düğümü `price`genişletin.

   ![Visual Studio'da XSLT hata ayıklama sırasında pencereyi izleyin](media/xslt-debugging-watch-window.png)

   Geçerli defter düğümü için defter fiyatının değerini görebilir ve değerle karşılaştırabilirsiniz. `$bookAverage` Kitap fiyatı ortalamanın altında olduğundan, hata ayıklama işlemine devam ettiğinizde `xsl:if` koşul başarılı olmalıdır.

## <a name="step-through-the-code"></a>Kodda adım atma

1. Devam etmek için **F5** tuşuna basın.

   İlk kitap düğümü durumu `xsl:if` tatmin ettiği için, kitap düğümü *ortalamanın altındaki xml* çıktı dosyasına eklenir. Hata ayıklama, stil sayfasındaki öğeye yeniden `xsl:if` yerleştirilene kadar yürütmeye devam ediyor. Hata ayıklayıcı şimdi *books.xml* dosyasındaki ikinci kitap düğümü üzerinde konumlandırılmıştır.

   Watch **1** `self::node()` penceresinde, değer ikinci kitap düğümünde değişir. Fiyat öğesinin değerini inceleyerek, fiyatın ortalamanın üzerinde olduğunu belirleyebilirsiniz, böylece `xsl:if` durum başarısız olmalıdır.

2. Devam etmek için **F5** tuşuna basın.

   İkinci kitap düğümü `xsl:if` koşulu karşılamadığından, kitap düğümü *ortalamanın altındaki xml* çıktı dosyasına eklenmez. Hata ayıklama, stil sayfasındaki öğeye yeniden `xsl:if` yerleştirilene kadar yürütmeye devam eder. Hata ayıklayıcı şimdi `book` *books.xml* dosyasındaki üçüncü düğüm üzerinde konumlandırılmıştır.

   Watch **1** `self::node()` penceresinde, değer üçüncü kitap düğümünde değişir. `price` Öğenin değerini inceleyerek, fiyatın ortalamanın altında olduğunu belirleyebilirsiniz. Koşul `xsl:if` başarılı olmalıdır.

3. Devam etmek için **F5** tuşuna basın.

   `xsl:if` Koşul tatmin olduğundan, üçüncü kitap *ortalamanın altında.xml* çıktı dosyasına eklenir. XML belgesindeki tüm kitaplar işlendi ve hata ayıklayıcı durdu.

## <a name="sample-files"></a>Örnek dosyalar

Aşağıdaki iki dosya izleyerek kullanılır.

### <a name="below-averagexsl"></a>ortalamanın altında.xsl

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

### <a name="booksxml"></a>Books.xml

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
