---
title: SharePoint için sayfalar oluşturuluyor | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015166"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint için sayfa oluşturma
  Bir SharePoint sitesi için uygulama sayfaları, site sayfaları, ana sayfalar ve sayfa düzenleri oluşturabilirsiniz.

 Visual Studio 'da şablon kullanarak uygulama sayfaları oluşturabilirsiniz. SharePoint Designer 'ı kullanarak site sayfaları, ana sayfalar ve sayfa düzenleri oluşturun. Daha sonra, bu sayfaları bir SharePoint projesinde kullanmak için Visual Studio 'ya aktarabilirsiniz.

 Ayrıca, geçişli stil sayfaları, ECMAScript ve Temalar kullanarak sayfaların görünümünü ve davranışını değiştirebilirsiniz.

## <a name="types-of-sharepoint-pages"></a>SharePoint sayfa türleri
 Aşağıdaki tabloda, bir SharePoint sitesinin içerdiği dört ana sayfa türü açıklanmaktadır.

|Sayfa türü|Description|
|---------------|-----------------|
|Uygulama sayfaları|Sayfanın özel kod içermesini istiyorsanız veya sayfanın birden çok site arasında paylaşılmasını istiyorsanız bir uygulama sayfası oluşturun. Aksi takdirde, bir site sayfası en iyi seçim olabilir.|
|Site sayfaları|Aşağıdaki görevlerden herhangi birini gerçekleştirmek istiyorsanız site sayfası oluşturun:<br /><br /> -Sayfayı bir SharePoint kitaplığına ekleyin.<br />-Dinamik Web Bölümleri ve Web Bölümü bölgeleri gibi özellikleri barındırmak için sayfayı etkinleştirin.<br />-Kullanıcıların SharePoint Designer kullanarak sayfayı özelleştirmesini sağlar.<br /><br /> Sayfanın özel kod içermesini istiyorsanız site sayfası oluşturmayın. Bir site sayfasına özel kod ekleyebilseniz de, kullanıcı SharePoint Designer 'ı kullanarak sayfayı özelleştiren kod çalışmayı durduruyor.|
|Ana sayfalar|Site sayfaları ve uygulama sayfaları için ortak bir yapı tanımlamak istiyorsanız bir ana sayfa oluşturun.|
|Sayfa düzenleri|Sayfa düzenleri öğesine özeldir [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ve site sayfaları ve uygulama sayfaları için ortak bir yapıyı daha ayrıntılı olarak tanımlamanızı sağlar.|

 Her sayfa türü için genel bir bakış için bkz. [yapı taşı: sayfalar ve Kullanıcı arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))ve [sayfa düzenleri ve ana sayfalar](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Uygulama sayfaları oluştur
 Visual Studio 'da bir **Uygulama sayfa** öğesi ekleyerek bir SharePoint projesine uygulama sayfaları oluşturabilirsiniz. Sayfaya denetimler ekleyebilir ve sonra kod ekleyerek denetim olaylarını işleyebilirsiniz.

 Sayfanın kod dosyasında kesme noktaları ayarlayabilir, hata ayıklayıcıyı başlatabilir ve ek yapılandırma adımları gerçekleştirmeden sayfayı yerel bir SharePoint sitesinde test edebilirsiniz. Daha fazla bilgi için bkz. [SharePoint Için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Site sayfaları, ana sayfalar ve sayfa düzenleri oluşturma
 SharePoint Designer kullanarak site sayfaları, ana sayfalar ve sayfa düzenleri oluşturabilirsiniz. Daha sonra, bu sayfaları Visual Studio 'ya aktarabilirsiniz. Visual Studio 'da kullanılabilen dağıtım veya kaynak denetimi özelliklerinden yararlanmak istiyorsanız sayfalarınızı içeri aktarın. Daha fazla bilgi için bkz. [mevcut bir SharePoint sitesinden öğeleri Içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Bu sayfaları içeri aktardıktan sonra değiştirmek zor olduğundan, bu sayfaları içeri aktarmadan önce tasarlamanız gerekir.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Geçişli stil sayfaları, ECMAScript ve Temalar oluşturma
 Visual Studio, SharePoint siteleri için Geçişli Stil Sayfaları (CSS), ECMAScript (JavaScript, JScript) veya Tema dosyaları geliştirmeye yönelik şablonlar sağlamaz. Bu dosyaları SharePoint SDK 'da bulunan veya SharePoint Designer gibi araçları kullanarak oluşturabilirsiniz.

 Bu dosyaları çözümünüze doğrudan ekleyebilmeniz veya içeri aktarabilirsiniz. Her iki durumda da, eklediğiniz her öğe için uygun eşlenmiş klasörleri oluşturmanız gerekir. Eşlenmiş bir klasör oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Geçişli Stil Sayfaları oluşturma hakkında daha fazla bilgi için bkz. [SharePoint Foundation 'da geçişli stil sayfaları sınıfı kullanımı](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Bir SharePoint çözümü için JavaScript ve JScript dosyaları oluşturma hakkında daha fazla bilgi için bkz. [ECMAScript Için temel aspx sayfası ayarlama](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Temalar hakkında daha fazla bilgi için bkz. [yapı taşı: sayfalar ve Kullanıcı arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)|Bir SharePoint ana sayfasıyla birleştirilmiş uygulama sayfaları: *. aspx* içeriğinin nasıl ekleneceğini açıklar.|
|[Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)|SharePoint sitesinde çalışan ASP.NET sayfaları oluşturmayı gösterir.|
|[İzlenecek yol: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Bir SharePoint sitesi için ASP.NET Web sayfasının nasıl tasarlanacağını ve hata ayıklanacağını gösterir.|
