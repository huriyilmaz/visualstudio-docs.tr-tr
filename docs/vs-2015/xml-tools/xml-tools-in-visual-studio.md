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
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845980"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio'daki XML Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genişletilebilir biçimlendirme dili (XML) *, verileri tanımlamaya yönelik biçim sağlayan bir biçimlendirme dilidir. Bu, içeriğin daha kesin bildirimlerini ve birden çok platformda daha anlamlı arama sonuçlarını kolaylaştırır. Ayrıca, XML sununun verilerin ayrılmasını de mümkün değildir. Örneğin, HTML 'de, tarayıcıya verileri kalın veya italik olarak göstermesini söylemek için Etiketler kullanabilirsiniz; XML 'de, yalnızca şehir adı, sıcaklık ve barometrik baskısı gibi verileri anlatmak için Etiketler kullanırsınız. XML 'de, verileri bir tarayıcıda sunmak için Genişletilebilir Stil sayfası dili (XSL) ve geçişli stil sayfaları (CSS) gibi stil sayfalarını kullanırsınız. XML, verileri sunudan ve işlemden ayırır. Bu, farklı stil sayfaları ve uygulamalar uygulayarak verileri istediğiniz gibi görüntülemenizi ve işlemenizi sağlar.

 XML, Web üzerinden teslim için optimize edilmiş bir SGML alt kümesidir. World Wide Web Konsorsiyumu (W3C) tarafından tanımlanır. Bu Standartlaştırma, yapılandırılmış verilerin tek tek ve uygulamalardan veya satıcıların bağımsız olmasını güvence altına alır.

 XML, ve ' nin birçok özelliğinin çekirdeğundan oluşur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Aşağıdaki konu listesi, ve ' de sunulan XML ile ilgili araçları ve özellikleri adlandırır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

 Daha fazla bilgi için, XML geliştiricileri için en son belgeleri, teknik bilgileri, indirmeleri, haber gruplarını ve diğer kaynakları sağlayan [XML Geliştirici Merkezi](https://msdn.microsoft.com/data/bb190600.aspx)' ne bakın.

## <a name="in-this-section"></a>Bu Bölümde
 [XML verileriyle çalışma](../xml-tools/working-with-xml-data.md) Verilerin işlendiği şekilde XML rolünü ele alır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [XSLT hata ayıklama](../xml-tools/debugging-xslt.md) XSLT hatalarını ayıklamak için Visual Studio hata ayıklayıcısını kullanma hakkındaki konuların bağlantılarını sağlar.

## <a name="reference"></a>Başvuru
 [Microsoft.VisualStudio.XmlDüzenleyicisi](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) [XML Düzenleyicisi](https://msdn.microsoft.com/library/ms255810.aspx) ayrıştırma ağacınıSystem.Xml aracılığıyla gösterir [ . ](https://msdn.microsoft.com/library/system.xml.linq.aspx) XML belgeleri için LINQ.

 [XML standartları başvurusu](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) XML, belge türü tanımı (DTD), XML şeması tanım dili (XSD) ve XSLT gibi XML teknolojileri hakkında bilgi sağlar.

 <xref:System.Xml?displayProperty=fullName> Ad alanını oluşturan sınıfları ve diğer öğeleri açıklar <xref:System.Xml> ve her öğe hakkında daha ayrıntılı bilgi için bağlantılar sağlar.

 <xref:System.Xml.Serialization?displayProperty=fullName> Ad alanını oluşturan sınıfları ve diğer öğeleri açıklar <xref:System.Xml.Serialization> ve her öğe hakkında daha ayrıntılı bilgi için bağlantılar sağlar.

## <a name="related-sections"></a>İlgili Bölümler
 [XML belge nesne modeli (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) <xref:System.Xml.XmlDocument> Ve ilişkili SıNıFLARıNıN W3C belge nesne modeli (çekirdek) düzey 1 ve düzey 2 ad alanı destek belirtimlerine uygun olduğunu açıklar.

 [XmlReader Ile XML okuma](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) <xref:System.Xml.XmlReader> BIR XML akışı üzerinden önbelleğe alınmamış, yalnızca iletme, XML verilerine salt okuma erişimi sağlar.

 [XmlWriter Ile xml yazma](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) ' <xref:System.Xml.XmlWriter> Nin önbelleğe alınmamış, salt ileri, XML akışları oluşturma ve W3C standardına uygun XML belgeleri oluşturmanıza yardımcı olduğunu açıklar.

 [XSLT dönüşümleri](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) <xref:System.Xml.Xsl.XslCompiledTransform> SıNıFıNıN XSLT 1,0 önerisi nasıl uyguladığını açıklar.

 [XPath veri modelini kullanarak XML verilerini işleme](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) <xref:System.Xml.XPath.XPathNavigator> Sınıfının bir veya nesnesinde depolanan xml verilerini nasıl işleyebileceğinizi açıklar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator>Sınıfı, XQuery 1,0 ve XPath 2,0 veri modelini temel alır ve XML verilerinde gezinmek ve bunları düzenlemek için kullanılabilir.

 [XML şema nesne modeli (som)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) <xref:System.Xml.Schema.XmlSchema> Bir şemayı yüklemek ve düzenlemek için bir sınıf sağlayarak xml şemaları oluşturmak ve işlemek için kullanılan sınıfları açıklar.
