---
title: SharePoint için sayfa oluşturuluyor | Microsoft Docs
description: Visual Studio bir şablon kullanarak SharePoint için uygulama sayfaları oluşturun. SharePoint tasarımcısını kullanarak site sayfaları, ana sayfalar ve sayfa düzenleri oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ea354e391be2f94e2d80c3c549219c3d9e1b0787
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726772"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint için sayfa oluşturma
  SharePoint sitesi için uygulama sayfaları, site sayfaları, ana sayfalar ve sayfa düzenleri oluşturabilirsiniz.

 Visual Studio bir şablon kullanarak uygulama sayfaları oluşturabilirsiniz. SharePoint tasarımcısını kullanarak site sayfaları, ana sayfalar ve sayfa düzenleri oluşturun. daha sonra, bu sayfaları bir SharePoint projesinde kullanmak için Visual Studio içeri aktarabilirsiniz.

 Ayrıca, geçişli stil sayfaları, ECMAScript ve Temalar kullanarak sayfaların görünümünü ve davranışını değiştirebilirsiniz.

## <a name="types-of-sharepoint-pages"></a>SharePoint sayfa türleri
 aşağıdaki tabloda, bir SharePoint sitesinin içerdiği dört ana sayfa türü açıklanmaktadır.

|Sayfa türü|Description|
|---------------|-----------------|
|Uygulama sayfaları|Sayfanın özel kod içermesini istiyorsanız veya sayfanın birden çok site arasında paylaşılmasını istiyorsanız bir uygulama sayfası oluşturun. Aksi takdirde, bir site sayfası en iyi seçim olabilir.|
|Site sayfaları|Aşağıdaki görevlerden herhangi birini gerçekleştirmek istiyorsanız site sayfası oluşturun:<br /><br /> -sayfayı bir SharePoint kitaplığına ekleyin.<br />-dinamik Web Bölümleri ve Web bölümü bölgeleri gibi özellikleri barındırmak için sayfayı etkinleştirin.<br />-kullanıcıların sayfayı SharePoint tasarımcı kullanarak özelleştirmesini sağlar.<br /><br /> Sayfanın özel kod içermesini istiyorsanız site sayfası oluşturmayın. bir site sayfasına özel kod ekleyebilseniz de, kullanıcı SharePoint tasarımcısını kullanarak sayfayı özelleştiren kod çalışmayı durduruyor.|
|Ana sayfalar|Site sayfaları ve uygulama sayfaları için ortak bir yapı tanımlamak istiyorsanız bir ana sayfa oluşturun.|
|Sayfa düzenleri|Sayfa düzenleri öğesine özeldir [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ve site sayfaları ve uygulama sayfaları için ortak bir yapıyı daha ayrıntılı olarak tanımlamanızı sağlar.|

 Her sayfa türü için genel bir bakış için bkz. [yapı taşı: sayfalar ve Kullanıcı arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))ve [sayfa düzenleri ve ana sayfalar](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Uygulama sayfaları oluştur
 bir SharePoint projesine **uygulama sayfası** öğesi ekleyerek Visual Studio uygulama sayfaları oluşturabilirsiniz. Sayfaya denetimler ekleyebilir ve sonra kod ekleyerek denetim olaylarını işleyebilirsiniz.

 sayfanın kod dosyasında kesme noktaları ayarlayabilir, hata ayıklayıcıyı başlatabilir ve herhangi bir ek yapılandırma adımı gerçekleştirmeden sayfayı yerel bir SharePoint sitesinde test edebilirsiniz. Daha fazla bilgi için bkz. [SharePoint Için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Site sayfaları, ana sayfalar ve sayfa düzenleri oluşturma
 SharePoint tasarımcısını kullanarak site sayfaları, ana sayfalar ve sayfa düzenleri oluşturabilirsiniz. Ardından, bu sayfaları Visual Studio içine aktarabilirsiniz. Visual Studio ' de bulunan dağıtım veya kaynak denetimi özelliklerinden yararlanmak istiyorsanız sayfalarınızı içeri aktarın. daha fazla bilgi için bkz. [mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Bu sayfaları içeri aktardıktan sonra değiştirmek zor olduğundan, bu sayfaları içeri aktarmadan önce tasarlamanız gerekir.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Geçişli stil sayfaları, ECMAScript ve Temalar oluşturma
 Visual Studio, SharePoint siteleri için Geçişli Stil Sayfaları (CSS), ECMAScript (JavaScript, JScript) veya tema dosyalarını geliştirmeye yönelik şablonlar sağlamaz. bu dosyaları, SharePoint SDK 'da bulunan kılavuzu veya SharePoint tasarımcısı gibi araçları kullanarak oluşturabilirsiniz.

 Bu dosyaları çözümünüze doğrudan ekleyebilmeniz veya içeri aktarabilirsiniz. Her iki durumda da, eklediğiniz her öğe için uygun eşlenmiş klasörleri oluşturmanız gerekir. Eşlenmiş bir klasör oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Geçişli Stil Sayfaları oluşturma hakkında daha fazla bilgi için, bkz. [SharePoint Foundation 'da Geçişli Stil Sayfaları sınıfı kullanımı](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). SharePoint çözümü için JavaScript ve JScript dosyaları oluşturma hakkında daha fazla bilgi için bkz. [ECMAScript için temel ASPX sayfası ayarlama](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Temalar hakkında daha fazla bilgi için bkz. [yapı taşı: sayfalar ve Kullanıcı arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)|SharePoint ana sayfasıyla birleştirilmiş uygulama sayfaları: *. aspx* içeriğinin nasıl ekleneceğini açıklar.|
|[Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)|SharePoint bir sitede çalışan ASP.NET sayfalarının nasıl oluşturulacağını gösterir.|
|[izlenecek yol: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|bir SharePoint sitesi için ASP.NET Web sayfası tasarlama ve hata ayıklamanın nasıl yapılacağını gösterir.|
