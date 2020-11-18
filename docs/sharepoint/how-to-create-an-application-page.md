---
title: 'Nasıl yapılır: uygulama sayfası oluşturma | Microsoft Docs'
description: Bir veya daha fazla SharePoint sitesi için Visual Studio 'da bir ASP.NET Web sayfası (uygulama sayfası olarak da bilinir) oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df52ca75ef99fe98158cb5f874e59fe4ee0c47b4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849863"
---
# <a name="how-to-create-an-application-page"></a>Nasıl yapılır: uygulama sayfası oluşturma
  Bir veya daha fazla SharePoint sitesi için ASP.NET Web sayfası oluşturabilirsiniz. SharePoint 'te, bu sayfalara uygulama sayfaları denir. Bir site sayfasının aksine, bir uygulama sayfası sayfanın arkasında çalışan kodu içerir. Daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Bir uygulama sayfası oluşturmak için

1. Visual Studio 'da bir SharePoint projesi açın veya oluşturun.

     Daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin.

3. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

4. **Yeni öğe Ekle** iletişim kutusunda, **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

5. SharePoint şablonları listesinde **uygulama sayfası**' nı seçin.

6. **Ad** kutusunda, uygulama sayfası için bir ad belirtin ve sonra **Ekle** düğmesini seçin.

     Visual Studio, projenize birkaç klasör ve dosya ekler. Bu dosyalar hakkında daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

     Visual Web Developer Designer 'ın **kaynak** görünümünde, ASP.NET sayfa dosyası görüntülenir. **Araç kutusu** ' ndan denetimler ekleyerek ve içeriği içerik yeryerlerine yerleştirerek sayfayı tasarlayabilmeniz gerekir. Daha fazla bilgi için bkz. [kaynak görünümü, Web sayfası tasarımcısı](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Denetim olaylarını işlemek istiyorsanız, uygulama sayfası için kod dosyasına kod ekleyin.

     Kod dosyası, ASP.NET sayfa dosyasının düğümünü genişletirseniz ve projenin diline bağlı olarak *. cs* veya *. vb* uzantılı bir dosya olduğunda görüntülenir. Uygulama sayfasının nasıl oluşturulacağını gösteren uçtan uca bir örnek için bkz. [Izlenecek yol: SharePoint uygulaması oluşturma sayfası](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [İzlenecek yol: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
