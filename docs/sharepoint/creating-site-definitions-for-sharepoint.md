---
title: SharePoint için site tanımları oluşturuluyor | Microsoft Docs
description: SharePoint için site tanımları oluşturun. site tanımları SharePoint sitesinin görünümünü ve davranışını ve varsayılan içerik ve işlevlerini tanımlar.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149370"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint için site tanımları oluşturma
  ' deki SharePoint site tanımı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , yeni bir SharePoint sitesi için temel görevi gören bir *site tanımı* oluşturmanızı sağlar. bu tanımlar yalnızca SharePoint sitesinin görünüm ve davranışını ve ayrıca varsayılan içerik ve işlevlerini belirlememe. Tanımda önceden yapılandırılmış listeleri, içerik türlerini, olay alıcılarını, görüntüleri ve diğer öğeleri yerleştirebilirsiniz. SharePoint, örneğin BLOG gibi bazı site tanımlarını içerir. BLOG site tanımına dayalı bir site oluşturduğunuzda, site, bir blog sitesinin gerektirdiği listeleri, Web bölümlerini ve diğer öğeleri içerir.

 Site tanımları hakkında daha fazla bilgi için bkz. [site şablonları ve tanımları](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Site tanımı projeleri
 içindeki site tanımı projeleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yalnızca bir SharePoint sitesinin ihtiyacı olan temel dosyaları sağlar; varsayılan bir işlev sağlamaz. İstediğiniz işlevselliği sağlamak için dosya ve içerik eklemeniz gerekir. İhtiyacınız olan dosyaları oluşturarak ve ekleyerek siteyi el ile oluşturabilirsiniz.

## <a name="feature-stapling"></a>Özellik Zımbalama
 ' De site tanımları oluşturmanın bir avantajı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , otomatik olarak *özellik zımbalama* Kullandır. Özellik zımbalama, işlevselliğini site tanımına eklemek yerine bir özelliği site tanımına iliştirir. Bunun yapılması, özelliği, özgün site tanımını değiştirmeden site tanımı kullanılarak oluşturulan herhangi bir siteye eklemenizi sağlar. Daha fazla bilgi için bkz. [özellik zımbalama](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Site tanımı proje bileşenleri
 Bir site tanımı çözümü oluşturduğunuzda, aşağıdaki varsayılan dosyalar **SiteDefinition** düğümüne eklenir.

|Dosya Adı|Açıklama|
|---------------|-----------------|
|*default. aspx*|yeni SharePoint sitesinin varsayılan ASPX giriş sayfası.|
|*onet.xml*|Yeni sitenin yapılandırmasını, site tanımı şablonunun bileşenlerini ve varsayılan davranışı belirtir. Bu ayarlar, etkin olan içerik türleri, varsayılan liste görünümleri, belge şablonu dosyaları ve sitede bulunan Web bölümleri gibi öznitelikleri içerebilir. varsayılan olarak, `Modules` bölüm SharePoint sitesine eklenecek dosyaları ve bunların nasıl yapılandırıldığını listeler.|
|*webtemp_ \<SiteDefinitionName>.xml*|**yeni SharePoint site** sayfasının **şablon seçimi** bölümünde görünen site tanımı yapılandırmasını belirtir.|

 Varsayılan olarak, tüm site tanımları *\<drive:> \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* klasöründe depolanır. Her site tanımının kendi alt klasörü vardır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Temel Site Tanımı Projesi Oluşturma](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|İçinde temel bir site tanımı projesinin oluşturulmasına adım adım yol gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Nasıl yapılır: özel site tanımı ve yapılandırması oluşturma](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|var olan bir site tanımını kopyalayarak ve sonra kopyayı değiştirerek SharePoint özel bir site tanımının nasıl oluşturulacağını açıklar.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|**yeni SharePoint site** sayfasının **şablon seçimi** bölümünde kullanılabilir olan site tanımlarını belirten özgün dosyayı tanımlar.|
|[SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)|SharePoint çözümlerinin genel kullanım için nasıl hazırlanacağını açıklar.|
|[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|kullanıcıların değiştirebileceği SharePoint bir sayfanın parçalarını nasıl oluşturabileceğiniz açıklanmaktadır.|
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|uygulama sayfalarında ve Web Bölümleri çalışan yeniden kullanılabilir denetimleri nasıl oluşturabileceğiniz açıklanmaktadır.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Projenizde bir Web sayfası açtığınızda görüntülenen tasarımcı 'nın nasıl kullanılacağını açıklar.|
|[ASP.NET Web sayfalarına genel bakış](/previous-versions/aspnet/428509ah(v=vs.100))|[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Web sayfalarının yapısı, sayfaların tarafından nasıl işlendiği [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ve [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfaların XHTML standartları ile uyumlu olan biçimlendirmeyi nasıl görüntüleyeceği hakkında genel bilgiler sağlar.|
|[ASP.NET Web sayfası sözdizimi](/previous-versions/aspnet/k33801s3(v=vs.100))|ASP.NET sayfasını oluşturan biçimlendirme öğelerini açıklar.|
|[ASP.NET Web sayfalarını programlama](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Sayfalarda olay işleyicilerinin nasıl oluşturulacağı [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ve istemci betiği ile nasıl çalışılacağı hakkında bilgi sağlar.|
|[Windows SharePoint Services programlama](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|' De sağlanmış olan yönetilen nesne modelinin nasıl kullanılacağını açıklar [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
