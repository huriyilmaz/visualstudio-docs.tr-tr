---
title: 'İzlenecek Yol: XSLT Hiyerarşisi Kullanma'
description: Bu kılavuzda yer alan adımları kullanarak, Visual Studio'de XSLT Hiyerarşisi aracını kullanarak başvurulan stil sayfalarında hata ayıklamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.openlocfilehash: 514331475913d6fc368f744379a6ddf21703b0ea22a394e660bce328fda6c68b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423546"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Adım adım kılavuz: XSLT hiyerarşisini kullanma

XSLT Hiyerarşisi aracı birçok XML geliştirme görevlerini basitleştiriyor. XSLT stil sayfası genellikle ve `includes` `imports` yönergelerini kullanır. Derleme asıl stil sayfalarından başlar, ancak XSLT stil sayfası derlemenin bir sonucu olarak hata gördüğünüzde, hata asıl stil sayfalarından farklı bir kaynaktan gelebilir. Hatayı düzeltmek veya stil sayfalarını düzenlemek, dahil edilen veya içe aktarılan stil sayfalarına erişim gerektirir. Hata ayıklayıcıda stil sayfası boyunca adım ekleme ve içeri aktarılan stil sayfaları açabilirsiniz. Ayrıca, dahil edilen stil sayfalarının bir veya daha fazlasının bir noktasında kesme noktası eklemek de iyi olabilir.

XSLT Hiyerarşisi aracının yararlı olduğu bir diğer senaryo da yerleşik şablon kurallarına kesme noktaları koymaktır. Şablon kuralları, stil sayfası her modu için oluşturulan ve düğümle eşleşen başka bir şablon olduğunda tarafından `xsl:apply-templates` çağrılan özel şablonlardır. XSLT hata ayıklayıcısı, yerleşik şablon kurallarında hata ayıklama uygulamak için dosyayı geçici klasördeki kurallarla oluşturur ve bunları asıl stil sayfasıyla birlikte derler. Bazı kodlardan koda adımlamadan, asıl stil sayfalarına dahil edilmiş stil sayfalarını bulmak veya yerleşik şablon kurallarıyla stil sayfalarını bulup `xsl:apply-template` açmak zor olabilir.

Bu konudaki örnek, başvurulan stil sayfalarında hata ayıklamayı gösteriyor.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Başvurulan stil sayfası içinde hata ayıklamak için

1. Bir XML belgesini Visual Studio. Bu örnek aşağıdaki belgeyi kullanır:

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

1. Aşağıdaki *xslincludefile.xsl dosyasını ekleyin:*

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

3. Aşağıdaki *xslinclude.xsl dosyasını* ekleyin:

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

4. yönergesi'ne bir kesme noktası `<xsl:include href="xslincludefile.xsl" />` ekleyin.

5. Hata ayıklamayı başlatın.

6. Hata ayıklayıcısı yönergede `<xsl:include href="xslincludefile.xsl" />` durduğunda, Adımla **düğmesine** basın. Hata ayıklama başvurulan stil sayfası içinde devam eder. Hiyerarşi görünür durumdadır ve tasarımcı doğru yolu görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT profil oluşturucusu](../xml-tools/xslt-profiler.md)
