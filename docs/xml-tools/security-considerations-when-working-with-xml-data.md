---
title: XML Verileriyle Çalışırken Dikkat Edilecek Güvenlik Konuları
description: XML düzenleyicisinde veya XSLT hata ayıklayıcıda XML verileriyle çalışırken güvenlik konuları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e98e18e3e01f53afa6b0a9ea3bdec94f2186f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351355"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML verileriyle çalışırken güvenlik konuları

Bu konuda, XML Düzenleyicisi veya XSLT hata ayıklayıcıyla çalışırken bilmeniz gereken güvenlik sorunları ele alınmaktadır.

## <a name="xml-editor"></a>XML düzenleyicisi

XML Düzenleyicisi, Visual Studio metin düzenleyiciyi temel alır. <xref:System.Xml> <xref:System.Xml.Xsl> XML işlemlerinin çoğunu işlemek için ve sınıflarını kullanır.

- XSLT dönüştürmeleri yeni bir uygulama etki alanında yürütülür. XSLT dönüşümleri *korumalı* değildir; diğer bir deyişle, bilgisayarınızın kod erişimi güvenlik ilkesi, XSLT stil sayfasının bulunduğu yere göre kısıtlanmış izinleri belirlemekte kullanılır. Örneğin, bir Internet konumundan stil sayfaları en kısıtlı izinlere sahiptir, ancak sabit sürücünüze kopyalanmış stil sayfaları tam güvenle çalışır.

- <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, yürütme sırasında daha hızlı performans IÇIN XSLT 'Yi Microsoft ara diline derlemek için kullanılır.

- Katalog dosyasındaki bir dış konuma işaret eden şemalar, XML Düzenleyicisi ilk kez yüklendiğinde otomatik olarak indirilir. <xref:System.Xml.Schema.XmlSchemaSet>Sınıfı, şemaları derlemek için kullanılır. XML Düzenleyicisi ile birlikte gelen Katalog dosyası herhangi bir dış şemaya yönelik bağlantılara sahip değildir. XML Düzenleyicisi şema dosyasını indirmeden önce, kullanıcının dış şemaya açıkça bir başvuru eklemesi vardır. HTTP indirme, XML Düzenleyicisi için **çeşitli Araçlar Seçenekler** sayfası aracılığıyla devre dışı bırakılabilir.

- XML Düzenleyicisi <xref:System.Net> şemaları indirmek için sınıfları kullanır

## <a name="xslt-debugger"></a>XSLT hata ayıklayıcısı

XSLT hata ayıklayıcı, ve ad alanından Visual Studio tarafından yönetilen hata ayıklama altyapısını ve sınıfları kullanır <xref:System.Xml> <xref:System.Xml.Xsl> .

- XSLT hata ayıklayıcısı her XSLT dönüşümünü bir korumalı uygulama etki alanında çalıştırır. Bilgisayarınızın kod erişimi güvenlik ilkesi, XSLT stil sayfasının bulunduğu yere göre kısıtlanmış izinleri belirlemekte kullanılır. Örneğin, bir Internet konumundan stil sayfaları en kısıtlı izinlere sahiptir, ancak sabit sürücünüze kopyalanmış stil sayfaları tam güvenle çalışır.

- XSLT stil sayfası sınıfı kullanılarak derlenir <xref:System.Xml.Xsl.XslCompiledTransform> .

- XSLT ifade değerlendirici yönetilen hata ayıklama altyapısı tarafından yüklenir. Yönetilen hata ayıklama altyapısı, tüm kodun kullanıcının yerel bilgisayarından çalıştırıldığını varsayar. Buna uygun olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT dosyasını kullanıcının yerel bilgisayarına indirir. Yürütme ayrıcalığının bir yükseltmesinde, kısıtlanmış izinlerle yeni bir uygulama etki alanındaki tüm XSLT dönüştürmeleri yürütülerek hafiflemesinin oluşma olasılığı

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanları](/dotnet/framework/app-domains/application-domains)