---
title: 'İzlenecek Yol: XSLT IntelliSense Kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adeab012e78d5f49ca94d1d8135aaf491839c767
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592444"
---
# <a name="walkthrough-using-xslt-intellisense"></a>İzlenecek Yol: XSLT IntelliSense Kullanma

Bu izlenecek yol, bazı özniteliklerin değerlerini otomatik olarak tamamlamak için XSLT IntelliSense 'in nasıl kullanılacağını gösterir.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>IntelliSense 'i xsl: WITH-param ve xsl: call-template öğeleri ad özniteliğinde kullanmak için

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. `<xsl:template name="msg23" match="msg23">` sonra imlecinizi yerleştirip **ENTER**tuşuna basın. Sonra aşağıdaki `xsl:call-template` öğesini yazmaya başlayın:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Şablon adları listesi, yazarken `xsl:call-template` öğesinin `name=""` özniteliğinde görüntülenir.

3. `<xsl:call-template name="localized-message">` sonra imlecinizi yerleştirip **ENTER**tuşuna basın. Sonra aşağıdaki `xsl:with-param` öğesini yazmaya başlayın:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Parametre adlarının listesi, `xsl:with-param` öğesinin `name=""` özniteliğinde görüntülenir.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Bir xsl: apply-templates öğesinin mode özniteliğinde IntelliSense kullanmak için

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. `<xsl:apply-templates select="phone" />` sonra imlecinizi yerleştirip **ENTER**tuşuna basın. Sonra aşağıdaki `xsl: apply-templates` öğesini yazmaya başlayın:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Şablon modlarının listesi, `xsl:apply-templates` öğesinin `mode=""` özniteliğinde görüntülenir.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>IntelliSense 'in stil sayfası-önek ve sonuç-önek öznitelikleri içinde bir xsl: Namespace-Alias öğesi

1. Yeni bir XSLT dosyası oluşturun ve aşağıdaki kodu kopyalayın:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. `<xsl:stylesheet version="1.0">` sonra imlecinizi yerleştirip **ENTER**tuşuna basın. Sonra aşağıdaki `xsl:namespace-alias` öğesini yazmaya başlayın:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Ön eklerin listesinin, `xsl:namespace-alias` öğesinin `stylesheet-prefix` ve `result-prefix` özniteliklerinde görünmediğine dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi IntelliSense özellikleri](../xml-tools/xml-editor-intellisense-features.md)
