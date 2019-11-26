---
title: XML Araçları
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ee0cf61f8ec2787894c6f67b8ac75424246c507
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297454"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio'daki XML Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genişletilebilir Biçimlendirme Dili (XML) * veri tanımlamak için bir biçim sağlayan bir biçimlendirme dilidir. Bu, birden çok platformda daha kesin bildirimleri içerik ve daha anlamlı arama sonuçlarının kolaylaştırır. Ayrıca, XML veri sunudan ayrımı sağlar. Örneğin, HTML etiketleri tarayıcıya kalın veya italik verileri görüntülemek için kullandığınız; XML etiketleri yalnızca şehir adı, sıcaklık ve barometric baskısı gibi verileri tanımlamak için kullanın. XML verilerini bir tarayıcıda sunmak için Genişletilebilir Stil Sayfası Dili (XSL) gibi stil sayfaları ve geçişli stil sayfaları (CSS) kullanırsınız. XML verileri, sunu ve işlem ayırır. Bu, görüntülemek ve farklı bir stil sayfaları ve uygulamaları uygulayarak istediğiniz verileri işlemek sağlar.

 XML Web üzerinden teslimat için optimize edilmiştir SGML bir alt kümesidir. Bu, World Wide Web Consortium (W3C) tarafından tanımlanır. Bu Standardizasyon Tekdüzen ve uygulamaları veya satıcılar bağımsız yapılandırılmış veri olacağını garanti eder.

 XML, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]birçok özelliğinin çekirdeğundan oluşur. Aşağıdaki konu listesi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]sunulan XML ile ilgili araçları ve özellikleri adlandırır.

 Daha fazla bilgi için, XML geliştiricileri için en son belgeleri, teknik bilgileri, indirmeleri, haber gruplarını ve diğer kaynakları sağlayan [XML Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkID=100176)' ne bakın.

## <a name="in-this-section"></a>Bu Bölümde
 [XML verileriyle çalışma](../xml-tools/working-with-xml-data.md) XML 'nin rolünü, verilerin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]işlendiği şekilde açıklar.

 [XSLT hata ayıklama](../xml-tools/debugging-xslt.md) XSLT hatalarını ayıklamak için Visual Studio hata ayıklayıcısını kullanma hakkındaki konuların bağlantılarını sağlar.

## <a name="reference"></a>Başvuru
 [Microsoft. VisualStudio. XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) HERHANGI bir XML belgesi için [System. xml. Linq](https://go.microsoft.com/fwlink/?LinkId=228250) aracılığıyla [XML düzenleyici](https://go.microsoft.com/fwlink/?LinkId=228249) ayrıştırma ağacını kullanıma sunar.

 [XML standartları başvurusu](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) XML, belge türü tanımı (DTD), XML şeması tanım dili (XSD) ve XSLT gibi XML teknolojileri hakkında bilgi sağlar.

 <xref:System.Xml?displayProperty=fullName>, <xref:System.Xml> ad alanını oluşturan sınıfları ve diğer öğeleri açıklar ve her öğe hakkında daha ayrıntılı bilgi için bağlantılar sağlar.

 <xref:System.Xml.Serialization?displayProperty=fullName>, <xref:System.Xml.Serialization> ad alanını oluşturan sınıfları ve diğer öğeleri açıklar ve her öğe hakkında daha ayrıntılı bilgi için bağlantılar sağlar.

## <a name="related-sections"></a>İlgili Bölümler
 [XML belge nesne modeli (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) <xref:System.Xml.XmlDocument> ve ilişkili sınıflarının W3C Belge Nesne Modeli (çekirdek) düzey 1 ve düzey 2 ad alanı destek belirtimlerine uygun olduğunu açıklar.

 [XmlReader Ile XML okuma](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) <xref:System.Xml.XmlReader>, bir XML akışı üzerinden önbelleğe alınmamış, yalnızca iletme, XML verilerine salt okuma erişimi sağlar.

 [XmlWriter Ile xml yazma](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) <xref:System.Xml.XmlWriter>, önbelleğe alınmamış, yalnızca iletme, XML akışları oluşturma ve W3C standardına uygun XML belgeleri oluşturmanıza yardımcı olur.

 [XSLT dönüşümleri](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının XSLT 1,0 önerisi nasıl uyguladığını açıklar.

 [XPath veri modelini kullanarak XML verilerini işleme](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) <xref:System.Xml.XPath.XPathNavigator> sınıfının bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesinde depolanan XML verilerini nasıl işleyebileceğinizi açıklar. <xref:System.Xml.XPath.XPathNavigator> sınıfı, XQuery 1,0 ve XPath 2,0 veri modelini temel alır ve XML verilerinde gezinmek ve bunları düzenlemek için kullanılabilir.

 [XML şema nesne modeli (som)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Bir şemayı yüklemek ve düzenlemek için bir <xref:System.Xml.Schema.XmlSchema> sınıfı sağlayarak XML şemaları oluşturmak ve işlemek için kullanılan sınıfları açıklar.
