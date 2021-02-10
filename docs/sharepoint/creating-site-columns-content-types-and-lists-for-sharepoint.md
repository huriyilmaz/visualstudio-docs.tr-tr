---
title: SharePoint için site sütunları, Içerik türleri ve listeler oluşturma | Microsoft Docs
titleSuffix: ''
description: SharePoint için site sütunları, içerik türleri ve listeler oluşturun. Visual Studio bu SharePoint öğesi türleri için proje öğesi şablonları sağlar.
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
ms.workload:
- office
ms.openlocfilehash: dfdf94f58c0fa7ba40d7c08309f8ea57949310df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949031"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>SharePoint için site sütunları, içerik türleri ve listeler oluşturma
  Visual Studio, her ikisi de site sütunları (veya *alanları*) içerebilen *listeler* ve *içerik türleri* de dahil olmak üzere birçok farklı temel SharePoint öğesi için proje öğesi şablonları sağlar. İçerik türleri ve listeleri için yeni tasarımcılar, bu öğelerin her zamankinden daha kolay oluşturulmasını sağlar.

## <a name="site-columns"></a>Site sütunları
 Site sütunları, bir SharePoint projesine ekleyebileceğiniz en temel öğelerden biridir. Bir site sütunu, bir kişi listesindeki bir kişinin telefon numarası, yorum veya şehir adı gibi bir veri türünü temsil eder.

 Yeni site sütunu proje öğesi şablonu, Visual Studio 'nun önceki sürümünden daha kolay site sütunları oluşturmayı kolaylaştırır. Yeni bir site sütunu oluşturduktan sonra, site sütununun *Elements.xml* dosyasındaki XML 'yi, görünen adı, veri türü ve site sütununun SharePoint 'te görünmesini istediğiniz grup gibi istediğiniz bilgileri içerecek şekilde değiştirebilirsiniz. Site sütunları hakkında daha fazla bilgi için bkz. [sütunlara giriş](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14)).

## <a name="content-types-and-lists"></a>İçerik türleri ve listeler
 İçerik türleri ve listeler, SharePoint 'teki en sık kullanılan öğeler arasındadır.

 Bir içerik türü, bir SharePoint listesi veya belge kitaplığındaki bir öğe kategorisi için meta verileri, iş akışını ve davranışı tanımlar. Örneğin, bir kişi listesinde veya bir görev listesinde bilgi için bir içerik türü oluşturabilirsiniz. Kişi içerik türü ad, e-posta, telefon numarası ve adres gibi sütunlar içerebilir. Site düzeyinde tanımladığınız bir içerik türü, sitedeki herhangi bir listeden veya belge kitaplığından bağımsızdır. SharePoint sitesindeki farklı listeler veya belge kitaplıkları ile aynı içerik türünü kullanabilirsiniz. Aynı liste veya belge kitaplığındaki çeşitli içerik türlerini de kullanabilirsiniz.

 Liste, SharePoint 'te başkalarıyla paylaşabileceğiniz bir bilgi koleksiyonudur. Listeler, veri içeren sütun satırlarından oluşur. Listelerden bazı örnekler şunlardır: bir görev listesi, kişiler listesi ve Duyurular listesi.

 Yeni Içerik türü ve liste tasarımcıları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] site içerik türlerini oluşturma, Visual Studio 'nun önceki sürümünden çok daha kolay ve daha sezgisel hale getirir. Kullanıcı arabirimi, içerik türlerini ve listeleri tanıdık bir şekilde görsel olarak oluşturmanıza ve Listelerdeki verileri sıralayıp gruplandırmanıza ve grup başlıklarını kullanmanıza olanak sağlar. İçerik türleri hakkında daha fazla bilgi için bkz. [Içerik türleri](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Listeler hakkında daha fazla bilgi için bkz. [liste formları](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) ve [liste görünümleri](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Özel içerik türünde kullanılan site sütunlarının nasıl oluşturulacağını gösterir. İçerik türü daha sonra özel bir listede kullanılır.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint 2010 ' de geliştirmeye başlama](/sharepoint/dev/)
