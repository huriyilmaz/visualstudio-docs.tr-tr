---
title: Web Bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015137"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma
  Visual Studio 'da, uygulama sayfaları ve SharePoint 'te çalışan Web Bölümleri tarafından tüketilen özel, yeniden kullanılabilir denetimler oluşturabilirsiniz. Bu denetimlere Kullanıcı denetimleri denir. Kullanıcı denetimi, bir ASP.NET Web sayfasına çok benzeyen bir bileşik denetim türüdür. var olan Web sunucusu denetimlerini ve işaretlemesini bir kullanıcı denetimine ekleyebilir ve denetimin özelliklerini ve yöntemlerini tanımlayabilirsiniz. Daha sonra bunları birim olarak davranan ASP.NET Web sayfalarına ekleyebilirsiniz.

## <a name="create-a-user-control"></a>Kullanıcı denetimi oluşturma
 Bir kullanıcı denetimi oluşturmak için, **boş bir SharePoint projesine** **Kullanıcı denetimi** ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint uygulama sayfası veya Web bölümü için Kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Bir **Kullanıcı denetim** öğesi eklediğinizde, Visual Studio projenizde bir klasör oluşturur ve sonra klasöre birkaç dosya ekler. Aşağıdaki tabloda her bir dosya açıklanmaktadır.

|Dosya|Description|
|----------|-----------------|
|Kullanıcı denetimi dosyası|Kullanıcı denetimini tanımlar. Bu dosyaya denetimler ve biçimlendirme ekleyerek kullanıcı denetimini tasarlayın.|
|Kod dosyası|Kullanıcı denetiminin arkasındaki kodu içerir. Bu dosyaya olayları işlemek için kod ekleyin.|
|Tasarımcı kod dosyası|Tasarımcı tarafından oluşturulan ve doğrudan düzenlenmemelidir bir kod içerir.|

## <a name="design-the-user-control"></a>Kullanıcı denetimini tasarlama
 Visual Studio 'da Visual Web Developer Designer kullanarak Kullanıcı denetimini tasarlayın. Bu tasarımcı, projenizde kullanıcı denetim dosyasını açıp **Tasarım** sekmesini seçtiğinizde görünür.

## <a name="consume-the-user-control"></a>Kullanıcı denetimini kullanma
 Kullanıcı denetimleri, bir uygulama sayfasına veya bir Web bölümüne dahil edilene kadar SharePoint 'te görünmez.

 Bir uygulama sayfasına kullanıcı denetimi eklemek için, ASP.NET Kullanıcı denetimini eklemek istediğiniz Web sayfasını açın. Tasarım görünümü geçin, sonra Çözüm Gezgini içindeki özel kullanıcı denetimi dosyanızı seçin ve sayfaya sürükleyin. ASP.NET Kullanıcı denetimi sayfaya eklenir ve tasarımcı, sayfanın Kullanıcı denetimini tanıması için gerekli olan @ Register yönergesini oluşturur. Artık denetimin ortak özellikleri ve yöntemleriyle birlikte çalışabilirsiniz.

 Bir Web bölümüne Kullanıcı denetimi eklemek için Kullanıcı denetimini Web Bölümü <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kod dosyasında Web Bölümü koleksiyonuna ekleyin. Aşağıdaki örnek bir Web Bölümü koleksiyonuna bir kullanıcı denetimi ekler <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> .

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Kullanıcı denetiminde hata ayıklama
 Bir kullanıcı denetiminde hata ayıklamak için, Kullanıcı denetiminin SharePoint projenizdeki bir uygulama sayfasına veya Web bölümüne eklendiğinden emin olun. Daha sonra, herhangi bir Visual Studio projesindeki kodda hata ayıklama yaptığınız gibi, Kullanıcı denetimindeki kodda hata ayıklayabilirsiniz.

 Visual Studio hata ayıklayıcısını başlattığınızda, Visual Studio SharePoint sitesini açar.

 SharePoint 'te, Kullanıcı denetimini içeren uygulama sayfasını açın. Kullanıcı denetimi bir Web bölümüne dahil ise, Web bölümünü SharePoint 'teki bir Web Bölümü sayfasına ekleyin.

 SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: SharePoint uygulama sayfası veya Web bölümü için Kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint 'te çalışan uygulama sayfaları ve Web Bölümleri tarafından tüketilen özel, yeniden kullanılabilir denetimler oluşturmayı gösterir.|
