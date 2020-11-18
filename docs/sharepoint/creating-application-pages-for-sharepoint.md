---
title: SharePoint için uygulama sayfaları oluşturma | Microsoft Docs
description: SharePoint için uygulama sayfaları oluşturun. Bir uygulama sayfası, SharePoint Web sitesinde kullanılmak üzere tasarlanan bir ASP.NET Web sayfasıdır.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1228ef551235fd616803d6e05057ee50f0ea7ec4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850448"
---
# <a name="create-application-pages-for-sharepoint"></a>SharePoint için uygulama sayfaları oluşturma
  Bir *uygulama sayfası* , SharePoint Web sitesinde kullanılmak üzere tasarlanan bir ASP.NET Web sayfasıdır. Uygulama sayfaları, ASP.NET sayfasının özelleşmiş bir türüdür. Bir uygulama sayfası ve standart ASP.NET sayfası arasındaki birincil fark, bir uygulama sayfasının bir SharePoint ana sayfasıyla birleştirilmiş içerik içermesinden bir uygulamadır. Ana sayfa, uygulama sayfalarının bir sitedeki diğer sayfalarla aynı görünümü ve davranışı paylaşmasına olanak sağlar.

 Visual Studio, tasarımcı kullanarak uygulama sayfaları tasarlamanızı sağlar. Tasarımcı, ana sayfada tanımlanan her içerik yer tutucusu için bir içerik alanı görüntüler. Denetimleri bu içerik bölümlerine sürükleyerek uygulama sayfasını tasarlayabilirsiniz.

## <a name="application-pages"></a>Uygulama sayfaları
 Uygulama sayfaları, sunucudaki tüm sitelerde paylaşılır, ancak site sayfası bir siteye özeldir. Daha fazla bilgi için [SharePoint sayfa türleri](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Varsayılan olarak, bir SharePoint sitesi oluştururken görüntülenen sayfaların çoğu site sayfalarıdır. Bir site sayfası, SharePoint sayfa kitaplığına eklenebilir. Kullanıcılar, SharePoint Designer gibi araçları kullanarak bir site sayfasını özelleştirebilir. Site sayfası, dinamik Web Bölümleri ve Web Bölümü bölgeleri gibi özellikleri de barındırabilir.

 Uygulama sayfaları bu işlemleri yapamazlar. Ancak, sayfanın özel kod içermesini istiyorsanız oluşturulacak en iyi sayfa türü bir uygulama sayfasıdır. Bir site sayfasına özel kod ekleyebilseniz de, kullanıcı SharePoint Designer gibi araçları kullanarak sayfayı özelleştiren kod çalışmayı durduruyor.

> [!NOTE]
> Visual Studio, bir SharePoint sitesi için site sayfaları oluşturmanıza yardımcı olan şablonlar sağlamaz. Daha fazla bilgi için bkz. [SharePoint sayfa türleri](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma
 Bir uygulama sayfası oluşturmak için bir SharePoint projesine bir **Uygulama sayfa** öğesi ekleyin. Bir uygulama sayfası oluşturduğunuzda, Visual Studio projenize aşağıdaki klasörleri ekler:

|Klasör|Açıklama|
|------------|-----------------|
|Düzenler|SharePoint dosya sisteminin _layouts sanal diziniyle eşlenir.|
|Düzenler alt klasörü|Uygulama sayfasını oluşturan dosyaları içerir. Varsayılan olarak, bu klasör projenizle aynı ada sahiptir. Bu klasörü dilediğiniz zaman yeniden adlandırabilirsiniz. Projeyi çalıştırdığınızda, Visual Studio bu klasörü SharePoint dosya sisteminin _layouts sanal dizinine dağıtır.|

 Visual Studio projenize aşağıdaki dosyaları ekler:

|Dosya|Açıklama|
|----------|-----------------|
|ASP.NET sayfa dosyası (*. aspx*)|Sayfayı tanımlayan XML işaretlemesini içerir.|
|Uygulama sayfası kod dosyası|Uygulama sayfasının arkasındaki kodu içerir. Bu dosyaya olayları işleyen kodu ekleyin.|
|Uygulama sayfa Tasarımcısı kod dosyası|Tasarımcı tarafından oluşturulan kodu içerir. Bu dosyayı doğrudan düzenlemeyin.|

## <a name="design-and-debug-an-application-page"></a>Uygulama sayfasında tasarım ve hata ayıklama
 Visual Studio 'daki tasarımcı görünümünü kullanarak bir uygulama sayfasının içeriğini tasarlayın. Bu tasarımcı, projenizde uygulama sayfasını açtığınızda görünür (bunu çift tıklayarak veya kısayol menüsünü açıp **Aç**' ı seçerek) ve ardından düzenleyicinin altındaki **Tasarım** düğmesini seçersiniz.

> [!NOTE]
> Sayfayı yalnızca tasarımcının **kaynak** görünümünde tasarlayabilirsiniz. Tasarımcı **Tasarım** görünümü uygulama sayfaları için devre dışı bırakılmıştır.

 Visual Studio 'da diğer SharePoint proje öğelerinde hata ayıklaması yaptığınız gibi, bir uygulama sayfasında hata ayıklayabilirsiniz. Visual Studio hata ayıklayıcısını başlattığınızda, Visual Studio SharePoint sitesini açar.

 Uygulama sayfasını görüntülemek için uygulama sayfasının konumuna el ile gitmeniz gerekir (örneğin: http://<em>SERVER_NAME</em>/_layouts/*Project_Name*/Applicationpage1.aspx).

 SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Ana sayfa seçin
 Varsayılan olarak, bir **uygulama sayfası** öğesi, projenizde hata ayıklamak için kullandığınız sitenin ana sayfasına başvurur. Bu sayfada v4. Master adı verilir ve SharePoint sitesinin **Ana sayfa galerisinde** listelenmiş olduğunu bulabilirsiniz.

 Uygulama öğesinin özniteliğini ayarlayarak uygulama sayfası tarafından hangi ana sayfanın kullanıldığını açıkça değiştirebilirsiniz `MasterPageFile` `Page` . (Örneğin: `MasterPageFile="~/_layouts/applicationv4.master"` ). Aslında, SharePoint sunucusunda dinamik ana sayfalar etkinleştirilmemişse bu özniteliği ayarlamanız gerekir. SharePoint 'teki ana sayfalar hakkında daha fazla bilgi için bkz. [ana sayfalar](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [Derinlemesine SharePoint Foundation geliştirme](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [ASP.NET’e genel bakış](/aspnet/overview)
- [ASP.NET Web Sayfaları](/aspnet/web-pages/index)
