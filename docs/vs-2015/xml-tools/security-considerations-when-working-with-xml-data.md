---
title: XML verileriyle çalışırken güvenlik konuları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656132"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML Verileriyle Çalışırken Dikkat Edilecek Güvenlik Konuları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, XML Düzenleyicisi veya XSLT hata ayıklayıcıyla çalışırken bilmeniz gereken güvenlik sorunları ele alınmaktadır.

## <a name="xml-editor"></a>XML Düzenleyicisi
 XML Düzenleyicisi, Visual Studio metin düzenleyiciyi temel alır. <xref:System.Xml> <xref:System.Xml.Xsl> XML işlemlerinin çoğunu işlemek için ve sınıflarını kullanır.

- XSLT dönüştürmeleri yeni bir uygulama etki alanında yürütülür. XSLT dönüşümleri *korumalı*değildir; diğer bir deyişle, bilgisayarınızın kod erişimi güvenlik ilkesi, XSLT stil sayfasının bulunduğu yere göre kısıtlanmış izinleri belirlemekte kullanılır. Örneğin, bir Internet konumundan stil sayfaları en kısıtlı izinlere sahiptir, ancak sabit sürücünüze kopyalanmış stil sayfaları tam güvenle çalışır.

- <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, yürütme sırasında daha hızlı performans IÇIN XSLT 'Yi Microsoft ara diline derlemek için kullanılır.

- Katalog dosyasındaki bir dış konuma işaret eden şemalar, XML Düzenleyicisi ilk kez yüklendiğinde otomatik olarak indirilir. <xref:System.Xml.Schema.XmlSchemaSet>Sınıfı, şemaları derlemek için kullanılır. XML Düzenleyicisi ile birlikte gelen Katalog dosyası herhangi bir dış şemaya yönelik bağlantılara sahip değildir. XML Düzenleyicisi şema dosyasını indirmeden önce, kullanıcının dış şemaya açıkça bir başvuru eklemesi vardır. HTTP indirme, XML Düzenleyicisi için **çeşitli Araçlar Seçenekler** sayfası aracılığıyla devre dışı bırakılabilir.

- XML Düzenleyicisi <xref:System.Net> şemaları indirmek için sınıfları kullanır

## <a name="xslt-debugger"></a>XSLT hata ayıklayıcısı
 XSLT hata ayıklayıcı, ve ad alanından Visual Studio tarafından yönetilen hata ayıklama altyapısını ve sınıfları kullanır <xref:System.Xml> <xref:System.Xml.Xsl> .

- XSLT hata ayıklayıcısı her XSLT dönüşümünü bir korumalı uygulama etki alanında çalıştırır. Bilgisayarınızın kod erişimi güvenlik ilkesi, XSLT stil sayfasının bulunduğu yere göre kısıtlanmış izinleri belirlemekte kullanılır. Örneğin, bir Internet konumundan stil sayfaları en kısıtlı izinlere sahiptir, ancak sabit sürücünüze kopyalanmış stil sayfaları tam güvenle çalışır.

- XSLT stil sayfası sınıfı kullanılarak derlenir <xref:System.Xml.Xsl.XslCompiledTransform> .

- XSLT ifade değerlendirici yönetilen hata ayıklama altyapısı tarafından yüklenir. Yönetilen hata ayıklama altyapısı, tüm kodun kullanıcının yerel bilgisayarından çalıştırıldığını varsayar. Buna uygun olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT dosyasını kullanıcının yerel bilgisayarına indirir. Yürütme ayrıcalığının bir yükseltmesinde, kısıtlanmış izinlerle yeni bir uygulama etki alanındaki tüm XSLT dönüştürmeleri yürütülerek hafiflemesinin oluşma olasılığı

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulama Etki Alanları](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
