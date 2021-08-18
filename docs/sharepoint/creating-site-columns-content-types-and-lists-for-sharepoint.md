---
title: SharePoint | için Site Sütunları, İçerik Türleri ve Listeleri Oluşturma Microsoft Docs
titleSuffix: ''
description: Web siteniz için site sütunları, içerik türleri ve SharePoint. Visual Studio, bu tür öğeler için proje öğesi SharePoint sağlar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 40ca1ca19e15e0e25e4decf6a3b932a3bcbf78b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149448"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Site sütunları, içerik türleri ve listeler oluşturma SharePoint
  Visual Studio, her ikisi de site sütunlarını (veya alanlarını)  dahil SharePoint içerik türleri dahil olmak üzere birçok farklı temel öğe öğesi için proje öğesi *şablonları sağlar.* İçerik türleri ve listeleri için yeni tasarımcılar, bu öğelerin oluşturulmasını hiç olmadığı kadar kolaylaştırır.

## <a name="site-columns"></a>Site sütunları
 Site sütunları, bir SharePoint projesine ekleyebilirsiniz. Site sütunu telefon numarası, açıklama veya kişi listesinde bir kişinin şehir adı gibi bir veri türünü temsil eder.

 Yeni site sütunu proje öğesi şablonu, site sütunlarının oluşturulmasını, site sütunlarının önceki sürümünden Visual Studio. Yeni bir site sütunu oluşturdukta, site sütununu *Elements.xml* dosyasındaki XML'i, görünen adı, veri türü ve site sütununu sütunda görünmesini istediğiniz grup gibi istediğiniz bilgileri içerecek şekilde SharePoint. Site sütunları hakkında daha fazla bilgi için [bkz. Sütunlara Giriş.](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14))

## <a name="content-types-and-lists"></a>İçerik türleri ve listeleri
 İçerik türleri ve listeleri, veri kaynaklarında en sık kullanılan SharePoint.

 İçerik türü, bir içerik listesinde veya belge kitaplığında bir öğe kategorisine ait meta SharePoint ve davranışı tanımlar. Örneğin, bir kişi listesinde veya görev listesinde bilgi için bir içerik türü oluşturabilirsiniz. Kişi içerik türü Ad, E-posta, Telefon Numarası ve Adres gibi sütunlar içerebilir. Site düzeyinde tanımladığınız içerik türü, sitenin herhangi bir listesinden veya belge kitaplığından bağımsızdır. Aynı içerik türünü, farklı listelerle veya belge kitaplıkları ile SharePoint kullanabilirsiniz. Aynı listede veya belge kitaplığında birden fazla içerik türü de kullanabilirsiniz.

 Liste, diğerleriyle paylaşabilirsiniz SharePoint bilgi koleksiyonudur. Listeler, veri içeren sütun satırlarından oluşur. Listelerden bazıları şunlardır: görev listesi, kişi listesi ve duyurular listesi.

 'daki yeni İçerik Türü ve Liste tasarımcıları, site içerik türleri oluşturmayı ve listeleri önceki sürüme göre çok daha kolay ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sezgisel hale Visual Studio. Kullanıcı arabirimi, içerik türlerini ve listeleri tanıdık bir şekilde görsel olarak oluşturmanın, listelerde verileri sıralamanın ve grup başlıklarını kullanmanın olanaklı olduğunu gösterir. İçerik türleri hakkında daha fazla bilgi için bkz. [İçerik Türleri.](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)) Listeler hakkında daha fazla bilgi için bkz. [Liste Formları](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) ve [Liste Görünümleri.](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14))

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Adım adım kılavuz: Site sütunu, içerik türü ve liste oluşturma SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Özel içerik türünde kullanılan site sütunlarının nasıl oluşturul olduğunu gösterir. İçerik türü daha sonra özel bir listede kullanılır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Başlarken SharePoint 2010'da geliştirme](/sharepoint/dev/)
