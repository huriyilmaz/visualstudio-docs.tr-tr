---
title: 'İzlenecek Yol: XSLT Hiyerarşisi Kullanma'
description: Bu yönergedeki adımları izleyerek, Visual Studio 'daki XSLT hiyerarşisi aracını kullanarak başvurulan bir stil sayfasında hata ayıklamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 94c8a26d75b92f9b8d51e3ca61f761985a5b4959
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875048"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>İzlenecek yol: XSLT hiyerarşisini kullanma

XSLT hiyerarşisi aracı birçok XML geliştirme görevini basitleştirir. XSLT stil sayfası genellikle `includes` ve yönergelerini kullanır `imports` . Derleme, asıl stil sayfasından başlar, ancak bir XSLT stil sayfası derlenirken bir hata gördüğünüzde, hata asıl stil sayfasından farklı bir kaynaktan gelebilir. Hata düzeltme veya stil sayfasını düzenlemede, eklenen veya içeri aktarılan stil sayfalarına erişim gerekebilir. Hata ayıklayıcı içindeki stil sayfasında adım adım dahil edilen ve içeri aktarılan stil sayfaları açılabilir ve bir veya daha fazla eklenen stil sayfasından bir veya daha fazla noktaya kesme noktası eklemek isteyebilirsiniz.

XSLT hiyerarşisi aracının yararlı olabilecek başka bir senaryo, yerleşik şablon kurallarına kesme noktaları koymaktadır. Şablon kuralları, stil sayfasının her bir modu için oluşturulan ve düğüm ile eşleşen başka bir şablon olmadığında çağrılan özel şablonlardır `xsl:apply-templates` . Yerleşik şablonlar kurallarında hata ayıklamayı uygulamak için, XSLT hata ayıklayıcı dosyayı geçici klasördeki kurallarla oluşturur ve bunları asıl stil sayfasıyla birlikte derler. Koddan kod içine `xsl:apply-template` adımlanmadan, asıl stil sayfasına dahil edilen stil sayfalarını bulmak veya yerleşik şablon kurallarıyla stil sayfasını bulmak ve açmak zor olabilir.

Bu konudaki örnekte, başvurulan bir stil sayfasında hata ayıklama gösterilmektedir.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Başvurulan bir stil sayfasında hata ayıklamak için

1. Visual Studio 'da bir XML belgesi açın. Bu örnek aşağıdaki belgeyi kullanır:

    ```xml
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

1. Aşağıdaki *xslıncludefile. xsl dosyasını* ekleyin:

    ```xml
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

3. Aşağıdaki *xslınclude. xsl* dosyasını ekleyin:

    ```xml
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

4. Yönergede bir kesme noktası ekleyin `<xsl:include href="xslincludefile.xsl" />` .

5. Hata ayıklamayı başlatın.

6. Hata ayıklayıcı yönergede durdurulduğunda, `<xsl:include href="xslincludefile.xsl" />` **adımla** düğmesine basın. Hata ayıklama, başvurulan stil sayfasında devam edebilir. Hiyerarşi görünür ve tasarımcı doğru yolu görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT profil oluşturucusu](../xml-tools/xslt-profiler.md)
