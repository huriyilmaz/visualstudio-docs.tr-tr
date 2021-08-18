---
title: XML Verileriyle Çalışırken Dikkat Edilecek Güvenlik Konuları
description: XML düzenleyicisinde veya XSLT hata ayıklayıcısında XML verileriyle çalışırken güvenlikle ilgili dikkat edilmesi gerekenler hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1860fa79502701a0adaa233302d99092c7724dde
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037739"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML verileriyle çalışırken güvenlikle ilgili dikkat edilmesi gerekenler

Bu konuda, XML düzenleyicisi veya XSLT hata ayıklayıcısı ile çalışırken hakkında bilgilisiniz gereken güvenlik sorunları ele almaktadır.

## <a name="xml-editor"></a>XML düzenleyicisi

XML düzenleyicisi, metin Visual Studio temel almaktadır. XML işlemlerinin çoğunu <xref:System.Xml> <xref:System.Xml.Xsl> işlemek için ve sınıflarını kullanarak.

- XSLT dönüştürmeleri yeni bir uygulama etki alanında yürütülür. XSLT dönüştürmeleri korumalı *alandadır;* diğer bir ifadeyle, XSLT stil sayfası nerede bulunduğuna bağlı olarak kısıtlı izinleri belirlemek için bilgisayarınızın kod erişim güvenlik ilkesi kullanılır. Örneğin, bir İnternet konumdaki stil sayfaları en kısıtlı izinlere sahipken, sabit sürücünize kopyalanan stil sayfaları Tam Güven ile çalışıyor.

- sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform> yürütme sırasında daha hızlı performans için XSLT'i Microsoft ara diline derlemek için kullanılır.

- Katalog dosyasındaki bir dış konumu işaret alan şemalar, XML düzenleyicisi ilk kez yüklendikten sonra otomatik olarak indirilir. sınıfı <xref:System.Xml.Schema.XmlSchemaSet> şemaları derlemek için kullanılır. XML düzenleyicisiyle birlikte alınan katalog dosyasının herhangi bir dış şemaya bağlantısı yok. XML düzenleyicisi şema dosyasını indirmeden önce kullanıcının dış şemaya açıkça bir başvuru eklemesi gerekir. HTTP indirme, XML düzenleyicisinin **Çeşitli Araçlar Seçenekleri sayfası aracılığıyla** devre dışı bırakılabilir.

- XML düzenleyicisi şemaları <xref:System.Net> indirmek için sınıfları kullanır

## <a name="xslt-debugger"></a>XSLT hata ayıklayıcısı

XSLT hata ayıklayıcısı, Visual Studio ve ad alanı sınıflarının yönetilen hata ayıklama <xref:System.Xml> altyapısını <xref:System.Xml.Xsl> kullanır.

- XSLT hata ayıklayıcısı her XSLT dönüştürmeyi korumalı bir uygulama etki alanında çalıştırır. XSLT stil sayfası nerede bulunduğuna bağlı olarak kısıtlı izinleri belirlemek için bilgisayarınızın kod erişim güvenlik ilkesi kullanılır. Örneğin, bir İnternet konumdaki stil sayfaları en kısıtlı izinlere sahipken, sabit sürücünize kopyalanan stil sayfaları Tam Güven ile çalışıyor.

- XSLT stil sayfası sınıfı kullanılarak <xref:System.Xml.Xsl.XslCompiledTransform> derlenmiş.

- XSLT ifade değerlendiricisi, yönetilen hata ayıklama altyapısı tarafından yüklenir. Yönetilen hata ayıklama altyapısı, tüm kodun kullanıcının yerel bilgisayarından çalıştır olduğunu varsayıyor. Buna uygun <xref:System.Xml.Xsl.XslCompiledTransform> olarak, sınıfı XSLT dosyasını kullanıcının yerel bilgisayarına indirir. Yürütme ayrıcalığında bir yükseltmenin oluşma olasılığı, kısıtlanmış izinlere sahip yeni bir uygulama etki alanında tüm XSLT dönüştürmeleri yürütülerek azaltılmıştır

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanları](/dotnet/framework/app-domains/application-domains)