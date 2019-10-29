---
title: SharePoint için site tanımları oluşturma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a75b7143412d360a7663e7cf94a1244d66d15a2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984530"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint için site tanımları oluşturma
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint site tanımı projesi, yeni bir SharePoint sitesi için temel görevi gören bir *site tanımı*oluşturmanızı sağlar. Bu tanımlar yalnızca SharePoint sitesinin görünüm ve davranışını ve ayrıca varsayılan içerik ve işlevlerini belirlememez. Tanımda önceden yapılandırılmış listeleri, içerik türlerini, olay alıcılarını, görüntüleri ve diğer öğeleri yerleştirebilirsiniz. SharePoint, örneğin BLOG gibi bazı site tanımlarını içerir. BLOG site tanımına dayalı bir site oluşturduğunuzda, site, bir blog sitesinin gerektirdiği listeleri, Web bölümlerini ve diğer öğeleri içerir.

 Site tanımları hakkında daha fazla bilgi için bkz. [site şablonları ve tanımları](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Site tanımı projeleri
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] içindeki site tanımı projeleri yalnızca bir SharePoint sitesinin ihtiyacı olan temel dosyaları sağlar; Varsayılan işlevsellik sağlamadıkları. İstediğiniz işlevselliği sağlamak için dosya ve içerik eklemeniz gerekir. İhtiyacınız olan dosyaları oluşturarak ve ekleyerek siteyi el ile oluşturabilirsiniz.

## <a name="feature-stapling"></a>Özellik Zımbalama
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] site tanımları oluşturmanın bir avantajı, otomatik olarak *özellik zımbalama*Kullandır. Özellik zımbalama, işlevselliğini site tanımına eklemek yerine bir özelliği site tanımına iliştirir. Bunun yapılması, özelliği, özgün site tanımını değiştirmeden site tanımı kullanılarak oluşturulan herhangi bir siteye eklemenizi sağlar. Daha fazla bilgi için bkz. [özellik zımbalama](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Site tanımı proje bileşenleri
 Bir site tanımı çözümü oluşturduğunuzda, aşağıdaki varsayılan dosyalar **SiteDefinition** düğümüne eklenir.

|Dosya Adı|Açıklama|
|---------------|-----------------|
|*default. aspx*|Yeni SharePoint sitesi için varsayılan ASPX giriş sayfası.|
|*onet. xml*|Yeni sitenin yapılandırmasını, site tanımı şablonunun bileşenlerini ve varsayılan davranışı belirtir. Bu ayarlar, etkin olan içerik türleri, varsayılan liste görünümleri, belge şablonu dosyaları ve sitede bulunan Web bölümleri gibi öznitelikleri içerebilir. Varsayılan olarak, `Modules` bölümünde SharePoint sitesine eklenecek dosyalar ve bunların nasıl yapılandırıldığı listelenmektedir.|
|*webtemp_\<SiteDefinitionName >. xml*|**Yeni SharePoint sitesi** sayfasının **şablon seçimi** bölümünde görünen site tanımı yapılandırmasını belirtir.|

 Varsayılan olarak, tüm site tanımları *\<Drive: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* klasöründe depolanır. Her site tanımının kendi alt klasörü vardır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Temel bir Site Tanımı Projesi Oluşturma](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]' de temel bir site tanımı projesi oluşturmaya adım adım yol gösterir.|
|[Nasıl yapılır: özel site tanımı ve yapılandırması oluşturma](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|SharePoint 'te, var olan bir site tanımını kopyalayarak ve sonra kopyayı değiştirerek özel bir site tanımı oluşturmayı açıklar.|
|[*WebTemp. xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|**Yeni SharePoint sitesi** sayfasının **şablon seçimi** bölümünde kullanılabilir olan site tanımlarını belirten özgün dosyayı tanımlar.|
|[SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)|SharePoint çözümlerinizin genel kullanım için nasıl hazırlanacağını açıklar.|
|[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|Kullanıcıların değiştirebileceği bir SharePoint sayfasının parçalarını nasıl oluşturabileceğiniz açıklanmaktadır.|
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Uygulama sayfalarında ve Web Bölümleri çalışan yeniden kullanılabilir denetimleri nasıl oluşturabileceğiniz açıklanmaktadır.|
|[Visual Web geliştiricisi](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Projenizde bir Web sayfası açtığınızda görüntülenen tasarımcı 'nın nasıl kullanılacağını açıklar.|
|[ASP.NET Web sayfalarına genel bakış](/previous-versions/aspnet/428509ah(v=vs.100))|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web sayfalarının yapısı, sayfaların [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]tarafından nasıl işlendiği ve [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfalarının XHTML standartlarıyla uyumlu olan biçimlendirmeyi nasıl görüntüleyeceği hakkında genel bilgiler sağlar.|
|[ASP.NET Web sayfası sözdizimi](/previous-versions/aspnet/k33801s3(v=vs.100))|Bir ASP.NET sayfasını oluşturan biçimlendirme öğelerini açıklar.|
|[ASP.NET Web sayfalarını programlama](/previous-versions/aspnet/0yt4zca8(v=vs.100))|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfalarında olay işleyicilerinin nasıl oluşturulacağı ve istemci betiği ile nasıl çalışılacağı hakkında bilgi sağlar.|
|[Windows SharePoint Services 'da programlama](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]içinde sunulan yönetilen nesne modelinin nasıl kullanılacağını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
