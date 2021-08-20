---
title: Korumalı Alanlı Çözüm konuları | Microsoft Docs
description: Microsoft SharePoint site koleksiyonu kullanıcılarının kendi özel kod çözümlerini karşıya yüklemesini sağlayan korumalı alanlı çözümleri keşfedin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 156ebc7fa17d53fd56cb8b069698f0bdf4b9a43c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092819"
---
# <a name="sandboxed-solution-considerations"></a>Korumalı alanlı çözümde dikkat edilmesi gerekenler
  *Korumalı alan çözümleri,* Microsoft SharePoint 2010'da site koleksiyonu kullanıcılarının kendi özel kod çözümlerini karşıya yüklemesini sağlayan bir özelliktir. Yaygın olarak kullanılan korumalı alan çözümü, kullanıcıların kendi Web Bölümleri.

 Korumalı alan SharePoint uygulaması, Web grubuyla sınırlı bir bölümü erişimi olan güvenli ve izlenen bir işlemde çalışır. Microsoft SharePoint 2010, korumalı alanlı çözümleri etkinleştirmek için özellikler, çözüm galerileri, çözüm izleme ve doğrulama çerçevesinin bir birleşimini kullanır.

## <a name="specify-project-trust-level"></a>Proje güven düzeyini belirtme
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Korumalı Alanlı Çözüm adlı bir Boole proje özelliği aracılığıyla korumalı *alanlı çözümleri destekler.* Bu özellik, proje içinde herhangi bir zamanda ya da projeyi Özelleştirme Sihirbazı'nda 7.000.000'de **SharePoint belirtilebilir.**

> [!NOTE]
> Proje *oluşturulduktan sonra korumalı* alan çözümü özelliğini değiştirmek doğrulama hatalarına neden olabilir.

 Korumalı Alanlı Çözüm özelliği false olarak ayarlanırsa veya *Grup* çözümü olarak dağıt seçeneğini seçerseniz çözüm, grup **kapsamlı bir çözüm olarak kabul** edilir.  Ancak Korumalı Alanlı Çözüm özelliği **true** olarak  ayarlanırsa veya sihirbazda Korumalı alanlı çözüm olarak dağıt seçeneğini seçerseniz çözüm bir grup **çözümünden** farklı şekilde kabul edilir.

## <a name="sharepoint-site-hierarchy"></a>SharePoint hiyerarşisi oluşturma
 Korumalı alanlı çözümlerin nasıl iş olduğunu anlamak için, SharePoint kapsamda hiyerarşik olduğunu bilmek yardımcı olur. Üst öğe Web grubu olarak bilinir ve diğer öğeler bunun alt öğesidir:

 Web Grubu

 Web Uygulaması A

 Site Koleksiyonu A1

 Site A1a

 Web Uygulaması B

 Site Koleksiyonu B1

 Site B1a

 Site B1b

 Site Koleksiyonu B2

 Site B2a

 Gördüğünüz gibi, Web gruplarında bir veya daha fazla Web uygulaması olabilir ve bu uygulamalar alt sitelere sahip olan bir veya daha fazla site koleksiyonu içerebilir. Bir site koleksiyonunda yapılan değişiklikler yalnızca o site koleksiyonunu etkiler ve diğerlerini etkilemez. Ancak, Web grubu düzeyinde yapılan değişiklikler, grup üzerinde tüm site koleksiyonlarını etkiler.

 Windows SharePoint Services (WSS) 3.0, çözümleri yalnızca grup düzeyine dağıtmaya olanak sağlar, ancak grup düzeyine (grup çözümü) veya site koleksiyonu düzeyine (korumalı alanlı çözüm) dağıtıma izin [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] verir.

## <a name="why-sandboxed-solutions"></a>Korumalı alanlı çözümler neden?
 3 WSS 3.0'da çözümler yalnızca grup düzeyinde dağıtılabilir. Bu, tüm Web grubu ve onun altında çalıştırılan diğer tüm site koleksiyonlarını ve uygulamalarını etkileyebilen zararlı veya kararsız çözümlerin dağıtılabilir olduğu anlamına geldi. Ancak korumalı alanlı çözümleri kullanarak çözümlerinizi, belirli bir site koleksiyonu olan grubu alt alanlara dağıtabilirsiniz. Ek koruma sağlamak için çözümün derlemesi ana işleme [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] yüklenmez (w3wp.exe).** Bunun yerine, ayrı bir işleme yüklenir (*SPUCWorkerProcess.exe).* Bu işlem izlenir ve grubu CPU döngülerini tüketen sıkı döngüler çalıştırma gibi zararlı etkinlikler gerçekleştiren korumalı alanlı çözümlerden korumak için kotalar ve azaltmalar uygulanır.

## <a name="site-collection-solution-gallery"></a>Site koleksiyonu çözüm galerisi
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010'un "site koleksiyonu çözüm galerisi" olarak bilinen bir özelliği vardır. Bu özele SharePoint 2010 Merkezi Yönetim sayfasından veya Site Eylemleri menüsünü açarak, **Site** **Ayarlar'i**  ve ardından  SharePoint sitesinde Galeriler'in altında Çözümler bağlantısını seçerek erişebilirsiniz. Çözüm galerileri, site koleksiyonu yöneticilerinin site koleksiyonlarında çözümleri yönetmesini sağlayan çözüm depolarıdır.

 Çözüm galerisi, sitenin kök Web'inde depolanan bir SharePoint kitaplığıdır. Çözüm galerisi, site şablonlarını değiştirir ve çözüm paketlerini destekler. Bir SharePoint paket (*.wsp*) dosyası karşıya yüklendiğinde korumalı alanlı bir çözüm olarak işlenir.

## <a name="sandboxed-solution-limitations"></a>Korumalı alanlı çözüm sınırlamaları
 Korumalı alanlı bir çözüm dağıtıldığında, SharePoint sahip olduğu güvenlik açıklarını azaltmaya yardımcı olmak için bu çözümün kullanımına açık olan işlev dizisi sınırlıdır. Bu sınırlamaların bazıları şunlardır:

- Korumalı alan çözümleri, dağıtılabilir çözüm öğelerinin sınırlı bir alt kümesine sahiptir. Site tanımları SharePoint iş akışları gibi güvenlik açığı olabilecek proje şablonları kullanılamaz.

- SharePoint, korumalı alanlı çözüm kodunu ana *uygulama havuzu*(SPUCWorkerProcess.exe) işleminden ayrı [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] bir *işlemde*(w3wp.exe) çalıştırır.

- Eşlenen klasörler projeye ek olamaz.

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Microsoft.Office derlemesinde türler. Sunucu korumalı alanlı çözümlerde kullanılamaz. Ayrıca, korumalı çözümlerde [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] yalnızca Microsoft.SharePoint derlemesinde türler kullanılabilir.

  Korumalı alanlı bir çözüm olarak bir SharePoint belirterek sunucuyu etkileyeceğini SharePoint önemlidir; Yalnızca SharePoint projesinin SharePoint hangi derlemelere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bağlanacağını belirler. Oluşturulan *.wsp* dosyasını etkilemez ve *.wsp* dosyasının Korumalı Alan çözümü özelliğiyle doğrudan ilişkili *verileri* yoktur.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Korumalı alanlı çözümlerde özellikler ve öğeler
 Korumalı alan çözümleri aşağıdaki özellikleri ve öğeleri destekler:

- İçerik Türleri/Alanları

- Özel eylemler

- Bildirimli iş akışları

- Olay alıcıları

- Özellikout'lar

- Tanımları Listele

- Örnekleri Listele

- Modül/dosyalar

- Gezinti

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Türeten tüm Web Bölümleri için destek`System.Web.UI.WebControls.WebParts.WebPart`

- Web Bölümleri

- WebTemplate özellik öğeleri *(Webtemp.xml)*

- Görsel Web Bölümleri

  Korumalı alanlı çözümler aşağıdaki özellikleri ve öğeleri desteklemez:

- Uygulama Sayfaları

- Özel Eylem Grubu

- Grup kapsamlı özellikler

- `HideCustomAction` öğesi

- Web Uygulaması kapsamlı özellikler

- Kod ile iş akışları

## <a name="see-also"></a>Ayrıca bkz.
- [Korumalı alan ve grup çözümleri arasındaki farklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)
