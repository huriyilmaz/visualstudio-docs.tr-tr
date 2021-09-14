---
title: Korumalı çözüm konuları | Microsoft Docs
description: Microsoft SharePoint 'de, site koleksiyonu kullanıcılarının kendi özel kod çözümlerini karşıya yüklemesine olanak sağlayan bir özellik olan korumalı çözümleri keşfet.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635558"
---
# <a name="sandboxed-solution-considerations"></a>Korumalı çözüm konuları
  *korumalı çözümler* , site koleksiyonu kullanıcılarının kendi özel kod çözümlerini karşıya yüklemesine olanak sağlayan Microsoft SharePoint 2010 ' deki bir özelliktir. ortak bir korumalı çözüm, kullanıcılar kendi Web Bölümleri karşıya yüklüyor.

 korumalı bir SharePoint uygulaması, Web grubunun sınırlı bir kısmına erişimi olan güvenli, izlenen bir işlemde çalışır. Microsoft SharePoint 2010, korumalı çözümleri etkinleştirmek için özelliklerin, çözüm galerlarının, çözüm izlemenin ve bir doğrulama çerçevesinin bir birleşimini kullanır.

## <a name="specify-project-trust-level"></a>Proje güven düzeyini belirtin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] korumalı *çözüm* adlı bir Boole proje özelliği aracılığıyla korumalı çözümleri destekler. bu özellik projede herhangi bir zamanda ayarlanabilir veya **SharePoint özelleştirme sihirbazında** projeyi oluşturduğunuzda belirlenebilir.

> [!NOTE]
> Projenin, oluşturulduktan sonra *Korumalı çözüm* özelliğini değiştirmek doğrulama hatalarına neden olabilir.

 *Korumalı çözüm* özelliği **false** olarak ayarlandıysa veya **Grup olarak dağıt** seçeneğini belirlerseniz çözüm, grup kapsamlı bir çözüm olarak değerlendirilir. Ancak, *Korumalı çözüm* özelliği **true** olarak ayarlanmışsa veya sihirbazda **Korumalı çözüm olarak dağıt** seçeneğini belirlerseniz çözüm bir grup çözümüyle farklı şekilde değerlendirilir.

## <a name="sharepoint-site-hierarchy"></a>SharePoint site hiyerarşisi
 korumalı çözümlerin nasıl çalıştığını anlamak için, SharePoint sitelerinin kapsamda hiyerarşik olduğunu öğrenmenize yardımcı olur. Üst öğe Web grubu olarak bilinir ve diğer öğeler bunun alt öğesidir:

 Web grubu

 Web uygulaması A

 Site koleksiyonu a1

 Site A1A

 Web uygulaması B

 Site koleksiyonu B1

 Site B1a

 Site B1B

 Site koleksiyonu B2

 Site b2a

 Görebileceğiniz gibi, Web grupları bir veya daha fazla Web uygulaması içerebilir ve bu da alt siteleri olabilecek bir veya daha fazla site koleksiyonu içerebilir. Bir site koleksiyonunda yapılan değişiklikler yalnızca o site koleksiyonunu etkiler ve başka hiçbir değildir. Ancak, Web grubu düzeyinde yapılan değişiklikler gruptaki tüm site koleksiyonlarını etkiler.

 Windows SharePoint Services (WSS) 3,0, çözümleri yalnızca grup düzeyine dağıtmanıza izin verir, ancak [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] grup düzeyine (grup çözümü) veya site koleksiyonu düzeyine (korumalı çözüm) dağıtmanıza olanak tanır.

## <a name="why-sandboxed-solutions"></a>Korumalı çözümler neden?
 WSS 3,0 ' de, çözümler yalnızca grup düzeyine dağıtılabilir. Bu, tüm Web grubunu ve bunun altında çalışan diğer tüm site koleksiyonlarını ve uygulamalarını etkileyen çözümlerin zararlı olabilecek veya kararsız hale getirilebilecek olması anlamına gelir. Ancak, korumalı çözümleri kullanarak çözümlerinizi belirli bir site koleksiyonu olan grubun alt alanına dağıtabilirsiniz. Ek koruma sağlamak için çözümün derlemesi ana [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] işleme (*w3wp.exe*) yüklenmez. Bunun yerine, ayrı bir işleme yüklenir (*SPUCWorkerProcess.exe*). Bu işlem izlenir ve grubu, CPU döngülerini kullanan sıkı döngüleri çalıştırmak gibi zararlı etkinlikleri gerçekleştiren korumalı çözümlerden korumak için kotalar ve azaltma uygular.

## <a name="site-collection-solution-gallery"></a>Site koleksiyonu Çözüm Galerisi
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010, "site koleksiyonu Çözüm Galerisi" olarak bilinen bir özelliğe sahiptir. bu özelliğe SharePoint 2010 merkezi yönetim sayfasından veya **site eylemleri** menüsünü açıp **site Ayarlar**' i seçerek ve ardından SharePoint sitesindeki **galeriler** bölümünde **çözümler** bağlantısını seçerek erişebilirsiniz. Çözüm galerileri, site koleksiyonu yöneticilerinin site koleksiyonlarında çözümleri yönetmesini sağlayan çözümlerin depolarıdır.

 çözüm galerisi, SharePoint sitesinin kök Web sitesinde depolanan bir belge kitaplığıdır. Çözüm Galerisi, site şablonlarının yerini alır ve çözüm paketlerini destekler. bir SharePoint çözüm paketi (*. wsp*) dosyası karşıya yüklendiğinde, bir korumalı çözüm olarak işlenir.

## <a name="sandboxed-solution-limitations"></a>Korumalı çözüm sınırlamaları
 korumalı bir çözüm dağıtıldığında, sahip olabileceği güvenlik açıklarını azaltmaya yardımcı olmak için SharePoint işlevselliği dizisi kullanılabilir. Bu sınırlamaların bazıları aşağıdakileri içerir:

- Korumalı çözümler için kullanılabilir dağıtılabilir çözüm öğelerinin kısıtlı bir alt kümesi vardır. site tanımları ve iş akışları gibi potansiyel olarak savunmasız SharePoint proje şablonları kullanılamaz.

- SharePoint, korumalı çözüm kodunu ana ** [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] uygulama havuzu (*w3wp.exe*) işleminden ayrı bir işlemde (SPUCWorkerProcess.exe) çalıştırır.

- Eşlenen klasörler projeye eklenemiyor.

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Microsoft. Office derlemesindeki türler. Sunucu, korumalı çözümler ' de kullanılamaz. ayrıca, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] korumalı çözümlerde yalnızca Microsoft. SharePoint derlemesindeki türler kullanılabilir.

  korumalı çözüm olarak bir SharePoint çözümü belirtmenin SharePoint sunucusu üzerinde hiçbir etkisi olmadığına dikkat edin. yalnızca SharePoint projenin, SharePoint ve hangi derlemelerin bağlandığı hakkında nasıl dağıtıldığını belirler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Oluşturulan *. wsp* dosyasını etkilemez ve *. wsp* dosyası, *Korumalı çözüm* özelliği ile doğrudan ilişkili hiçbir veri içermez.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Korumalı çözümlerdeki yetenekler ve öğeler
 Korumalı çözümler aşağıdaki özellikleri ve öğeleri destekler:

- İçerik türleri/alanları

- Özel Eylemler

- Bildirim temelli iş akışları

- Olay alıcıları

- Özellik belirtme çizgileri

- Liste tanımları

- Liste örnekleri

- Modül/dosyalar

- Gezinti

- *Onet.xml*

- Spitemeventalıcısı

- Splisteventalıcısı

- SPWebEventReceiver

- öğesinden türetilen tüm Web Bölümleri için destek`System.Web.UI.WebControls.WebParts.WebPart`

- Web Bölümleri

- WebTemplate özellik öğeleri ( *Webtemp.xml* yerine)

- görsel Web Bölümleri

  Korumalı çözümler aşağıdaki özellikleri ve öğeleri desteklemez:

- Uygulama sayfaları

- Özel eylem grubu

- Grup kapsamlı özellikler

- `HideCustomAction` öğesi

- Web uygulaması kapsamlı özellikler

- Kod içeren iş akışları

## <a name="see-also"></a>Ayrıca bkz.
- [Korumalı ve Grup çözümleri arasındaki farklılıklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)
