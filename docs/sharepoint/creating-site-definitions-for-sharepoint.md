---
title: SharePoint | için Site Tanımları Oluşturma Microsoft Docs
description: Uygulama için site tanımları SharePoint. Site tanımları, sitenin görünümünü ve davranışını SharePoint içeriğini ve işlevselliğini belirler.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2d0d97586b1f3f9f62e992aea3c5a480f538e018
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635625"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint için site tanımları oluşturma
  'SharePoint Site Tanımı projesi, yeni bir site için temel olarak görev alan bir site [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tanımı SharePoint sağlar.  Bu tanımlar yalnızca sitenin görünümünü ve davranışını değil, SharePoint ve işlevselliğini de belirler. Tanımda önceden yapılandırılmış listeler, içerik türleri, olay alıcıları, görüntüler ve diğer öğeleri koyabilirsiniz. SharePoint blog gibi bazı site tanımları içerir. BLOG sitesi tanımını temel alan bir site oluşturma, sitenin bir site için gerekli olan listeleri, Web bölümlerini ve diğer öğeleri içerir.

 Site tanımları hakkında daha fazla bilgi için [bkz. Site Şablonları ve Tanımları.](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14))

## <a name="site-definition-projects"></a>Site tanımı projeleri
 içinde site tanımı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeleri yalnızca bir sitenin SharePoint temel dosyaları sağlar; varsayılan işlevler sağlamaz. Istediğiniz işlevselliği sağlamak için dosya ve içerik eklemeniz gerekir. Siteyi el ile, ihtiyacınız olan dosyaları oluşturarak ve ekleyerek oluşturabilirsiniz.

## <a name="feature-stapling"></a>Özellik eskiterek
 içinde site tanımları oluşturmanın bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avantajı, otomatik olarak Özellik *Eskiterek özelliğini kullanmalarıdır.* Özellik Eskime özelliği, işlevselliğini site tanımına eklemek yerine bir site tanımına iliştiriyor. Bunu yapmak, özgün site tanımını değiştirmeden site tanımı kullanılarak oluşturulan herhangi bir siteye özelliği eklemenize olanak sağlar. Daha fazla bilgi için [bkz. Özellik Eskiterek.](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12))

## <a name="site-definition-project-components"></a>Site tanımı proje bileşenleri
 Bir site tanımı çözümü oluşturdukta, aşağıdaki varsayılan dosyalar **SiteDefinition düğümüne** eklenir.

|Dosya Adı|Açıklama|
|---------------|-----------------|
|*Default.aspx*|Yeni uygulama sitesi için varsayılan ASPX SharePoint sayfası.|
|*onet.xml*|Yeni sitenin yapılandırmasını, site tanımı şablonunun bileşenlerini ve varsayılan davranışı belirtir. Bu ayarlar, etkinleştirilen içerik türleri, varsayılan liste görünümleri, belge şablonu dosyaları ve siteye dahil edilen Web bölümleri gibi öznitelikleri içerebilir. Varsayılan olarak, `Modules` bölümünde, SharePoint siteye eklenecek dosyalar ve bunların nasıl yapılandırıldıkları listelenmiştir.|
|*webtemp_ \<SiteDefinitionName>.xml*|Yeni Uygulama Sitesi sayfasının Şablon Seçimi **bölümünde görünen** site tanımı **yapılandırmalarını SharePoint** belirtir.|

 Varsayılan olarak, tüm site tanımları *\<drive:> \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates klasöründe* depolanır. Her site tanımının kendi alt klasörü vardır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Temel Site Tanımı Projesi Oluşturma](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|içinde temel bir site tanımı projesi oluşturma adım adım size yol [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.|
|[Nasıl: Özel Site Tanımı ve Yapılandırması Oluşturma](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Mevcut bir site tanımını kopyalayıp kopyayı değiştirerek SharePoint site tanımı oluşturma hakkında bilgi sağlar.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Yeni Uygulama Sitesi sayfasının Şablon Seçimi bölümünde bulunan site **tanımlarını** **belirten özgün SharePoint açıklar.**|
|[Yerelleştirme SharePoint yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md)|Genel kullanım için SharePoint çözümlerinizin nasıl hazır olduğunu açıklar.|
|[SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|Bir uygulama sayfasının kullanıcıların değiştire SharePoint bölümlerini nasıl oluşturabilirsiniz?|
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Uygulama sayfalarında ve uygulama sayfalarında çalıştırarak yeniden kullanılabilir denetimler oluşturma Web Bölümleri.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Projeniz içinde bir Web sayfası a0 aken görüntülenen tasarımcının nasıl kullanıcazı açıklar.|
|[ASP.NET Web Sayfalarına Genel Bakış](/previous-versions/aspnet/428509ah(v=vs.100))|Web sayfalarının yapısı, sayfaların tarafından nasıl işlenmeleri ve sayfaların XHTML standartlarına uygun işaretlemeyi görüntülemesi [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] hakkında genel bilgiler [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sağlar.|
|[ASP.NET Web Sayfası Söz Dizimi](/previous-versions/aspnet/k33801s3(v=vs.100))|Bir sayfayı ASP.NET açıklar.|
|[Web ASP.NET Programlama](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Sayfalarda olay işleyicileri oluşturma ve [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] istemci betiğiyle çalışma hakkında bilgi sağlar.|
|[Windows SharePoint Services'da programlama](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|içinde sağlanan yönetilen nesne modelinin nasıl kullanılası [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] açıklanmıştır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
