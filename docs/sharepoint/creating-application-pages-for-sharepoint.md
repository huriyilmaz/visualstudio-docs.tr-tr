---
title: SharePoint | için Uygulama Sayfaları Oluşturma Microsoft Docs
description: Uygulama sayfaları oluşturun SharePoint. Uygulama sayfası, ASP.NET web sitesinde kullanım için tasarlanmış bir web SharePoint sayfasıdır.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 035c3b952fd16dd8aa4adf3ffb95542fe39464ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726774"
---
# <a name="create-application-pages-for-sharepoint"></a>SharePoint için uygulama sayfaları oluşturma
  Uygulama *sayfası,* ASP.NET web sitesinde kullanım için tasarlanmış bir web SharePoint sayfasıdır. Uygulama sayfaları, özel bir ASP.NET t'tir. Bir uygulama sayfası ile standart bir ASP.NET arasındaki temel fark, bir uygulama sayfasının bir uygulama ana sayfasıyla birleştirilmiş SharePoint içeriği içerdiğidir. Ana sayfa, uygulama sayfalarının bir sitenin diğer sayfalarıyla aynı görünüm ve davranışı paylaşmalarını sağlar.

 Visual Studio, bir tasarımcı kullanarak uygulama sayfaları tasarlamaya olanak sağlar. Tasarımcı, bir ana sayfada tanımlanan her içerik yer tutucusu için bir içerik alanı görüntüler. Denetimleri bu içerik alanlarına sürükleyerek uygulama sayfasını tasarleyebilirsiniz.

## <a name="application-pages"></a>Uygulama sayfaları
 Uygulama sayfaları sunucu üzerinde tüm sitelerde paylaşılırken, site sayfası bir siteye özgü olur. Daha fazla bilgi için [SharePoint Türleri'ne bakın.](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))

 Varsayılan olarak, bir site oluşturmada görünen sayfaların SharePoint site sayfalarıdır. Site sayfası, bir site SharePoint eklenebilir. Kullanıcılar Site Tasarımcısı gibi araçları kullanarak bir site SharePoint özelleştirebilirsiniz. Bir site sayfası, dinamik veri alanları ve Web Web Bölümleri alanları gibi özellikleri de barındırabilirsiniz.

 Uygulama sayfaları bunları yapılamaz. Ancak, uygulama sayfası, sayfanın özel kod içermesi için oluşturulabilir en iyi sayfa t t'dır. Bir site sayfasına özel kod ekleyebilirsiniz ancak kullanıcı sayfayı Özel Tasarımcı gibi araçları kullanarak özelleştirse de kod SharePoint durur.

> [!NOTE]
> Visual Studio, bir site için site sayfaları oluşturmanıza yardımcı olacak SharePoint sağlamaz. Daha fazla bilgi için [bkz. SharePoint Türleri.](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma
 Uygulama sayfası oluşturmak için bir uygulama **projesine Uygulama** Sayfası SharePoint ekleyin. Bir uygulama sayfası sanız Visual Studio aşağıdaki klasörleri projenize ekler:

|Klasör|Description|
|------------|-----------------|
|Düzenler|Haritalar sisteminin _layouts sanal dizinine SharePoint seçin.|
|Düzenler alt klasörü|Uygulama sayfasını içeren dosyaları içerir. Varsayılan olarak, bu klasör projenizin adıyla aynı adı kullanır. Bu klasörü istediğiniz zaman yeniden adlandırabilirsiniz. Projeyi çalıştırarak Visual Studio, bu klasörü dosya sisteminin _layouts sanal dizinine SharePoint dağıtır.|

 Visual Studio projenize aşağıdaki dosyaları ekler:

|Dosya|Description|
|----------|-----------------|
|ASP.NET dosyası (*.aspx*)|Sayfayı tanımlayan XML işaretlemesini içerir.|
|Uygulama sayfası kod dosyası|Uygulama sayfasının ardındaki kodu içerir. Bu dosyaya olayları işlemek için kod ekleyin.|
|Uygulama sayfası tasarımcısı kod dosyası|Tasarımcı tarafından oluşturulan kodu içerir. Bu dosyayı doğrudan düzenleme.|

## <a name="design-and-debug-an-application-page"></a>Uygulama sayfası tasarlama ve hata ayıklama
 Uygulama sayfasının içeriğini, uygulama sayfasındaki tasarımcı görünümünü kullanarak Visual Studio. Bu tasarımcı, projenizin uygulama sayfasını açıp (buna çift tıklayarak veya kısayol menüsünü açıp **Aç'ı**  seçerek) ve ardından düzenleyicinin en altındaki Tasarım düğmesini seçerek görünür.

> [!NOTE]
> Sayfayı yalnızca tasarımcının **Kaynak görünümünde** tasarleyebilirsiniz. **Tasarımcının** Tasarım görünümü, uygulama sayfaları için devre dışı bırakıldı.

 Uygulama sayfasındaki diğer proje öğelerinde olduğu gibi SharePoint hata ayıklaması Visual Studio. Hata ayıklayıcısını Visual Studio, Visual Studio siteyi SharePoint açar.

 Uygulama sayfasını görüntülemek için uygulama sayfasının konumunu el ile gitmelisiniz (örneğin: http://<em>Server_Name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Projelerde hata ayıklama hakkında daha fazla bilgi SharePoint bkz. [SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md)

## <a name="choose-a-master-page"></a>Ana sayfa seçme
 Varsayılan olarak, **bir Uygulama Sayfası** öğesi projenizin hata ayıklaması için kullanmakta olduğu sitenin ana sayfasına başvurur. Bu sayfa v4.master olarak adlandırılmıştır ve sitenin Ana Sayfa **Galerisinde** SharePoint bulabilirsiniz.

 Uygulama öğesinin özniteliğini ayarerek uygulama sayfası tarafından kullanılan ana `MasterPageFile` sayfayı açıkça `Page` değiştirebilirsiniz. (Örneğin: `MasterPageFile="~/_layouts/applicationv4.master"` ). Aslında, dinamik ana sayfalar sunucu üzerinde etkinleştirilmediyse bu özniteliği SharePoint gerekir. Ana sayfalarda ana sayfalar hakkında daha fazla SharePoint bkz. [Ana Sayfalar.](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint Derinlemesine Temel Geliştirme](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [ASP.NET’e genel bakış](/aspnet/overview)
- [ASP.NET Web Sayfaları](/aspnet/web-pages/index)
