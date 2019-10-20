---
title: 'İzlenecek yol: XSLT hiyerarşisini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46e6acc8f65a9c9589348508f57cc75b04c61ccc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669558"
---
# <a name="walkthrough-using-xslt-hierarchy"></a>İzlenecek Yol: XSLT Hiyerarşisi Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT hiyerarşisi aracı birçok XML geliştirme görevini basitleştirir. XSLT stil sayfası genellikle `includes` ve `imports` yönergelerini kullanır. Derleme, asıl stil sayfasından başlar, ancak bir XSLT stil sayfası derlenirken bir hata gördüğünüzde, hata asıl stil sayfasından farklı bir kaynaktan gelebilir. Hata düzeltme veya stil sayfasını düzenlemede, eklenen veya içeri aktarılan stil sayfalarına erişim gerekebilir. Hata ayıklayıcı içindeki stil sayfasında adım adım dahil edilen ve içeri aktarılan stil sayfaları açılabilir ve bir veya daha fazla eklenen stil sayfasından bir veya daha fazla noktaya kesme noktası eklemek isteyebilirsiniz.

 XSLT hiyerarşisi aracının yararlı olabilecek başka bir senaryo, yerleşik şablon kurallarına kesme noktaları koymaktadır. Şablon kuralları, stil sayfasının her bir modu için oluşturulan ve düğüm ile eşleşen başka bir şablon olmadığında `xsl:apply-templates` tarafından çağrılan özel şablonlardır. Yerleşik şablonlar kurallarında hata ayıklamayı uygulamak için, XSLT hata ayıklayıcı dosyayı geçici klasördeki kurallarla oluşturur ve bunları asıl stil sayfasıyla birlikte derler. Bazı `xsl:apply-template` koda adımlamadan, asıl stil sayfasına dahil edilen stil sayfalarını bulmak veya yerleşik şablon kurallarıyla stil sayfasını bulmak ve açmak zor olabilir.

 Bu konudaki örnekte, başvurulan bir stil sayfasında hata ayıklama gösterilmektedir.

### <a name="procedure-title"></a>Yordam başlığı

1. Visual Studio 'da bir XML belgesi açın. Bu örnek, aşağıdaki `collection.xml` belgesini kullanır.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

2. Aşağıdaki `xslincludefile.xsl` ekleyin:

    ```
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. Şu `xslinclude.xsl` dosyasını ekleyin:

    ```
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. Yönergede bir kesme noktası ekleyin: `<xsl:include href="xslincludefile.xsl" />`

5. Hata ayıklamayı başlatın.

6. Hata ayıklayıcı yönerge `<xsl:include href="xslincludefile.xsl" />` durdurulduğunda, adımla düğmesine basın. Hata ayıklamanın başvurulan stil sayfasında devam olabileceğini unutmayın. Hiyerarşi görünür ve tasarımcı doğru yolu görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek Yol: XSLT Profil Oluşturucusu](../xml-tools/walkthrough-xslt-profiler.md)
