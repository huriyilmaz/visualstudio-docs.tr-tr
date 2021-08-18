---
title: 'Nasıl yapılır: uygulama sayfası oluşturma | Microsoft Docs'
description: bir veya daha fazla SharePoint sitesi için Visual Studio bir ASP.NET web sayfası (uygulama sayfası olarak da bilinir) oluşturun.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 211bba75c6acee1a820a2b8b4adaefb508818a04
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060082"
---
# <a name="how-to-create-an-application-page"></a>Nasıl yapılır: uygulama sayfası oluşturma
  bir veya daha fazla SharePoint sitesi için ASP.NET web sayfası oluşturabilirsiniz. SharePoint, bu sayfalara uygulama sayfaları denir. Bir site sayfasının aksine, bir uygulama sayfası sayfanın arkasında çalışan kodu içerir. Daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Bir uygulama sayfası oluşturmak için

1. Visual Studio, bir SharePoint projesi açın veya oluşturun.

     daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin.

3. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

4. **yeni öğe ekle** iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

5. SharePoint şablonları listesinde **uygulama sayfası**' nı seçin.

6. **Ad** kutusunda, uygulama sayfası için bir ad belirtin ve sonra **Ekle** düğmesini seçin.

     Visual Studio projenize birkaç klasör ve dosya ekler. Bu dosyalar hakkında daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

     Visual Web Developer designer 'ın **kaynak** görünümünde ASP.NET sayfa dosyası görüntülenir. **Araç kutusu** ' ndan denetimler ekleyerek ve içeriği içerik yeryerlerine yerleştirerek sayfayı tasarlayabilmeniz gerekir. Daha fazla bilgi için bkz. [kaynak görünümü, Web sayfası tasarımcısı](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Denetim olaylarını işlemek istiyorsanız, uygulama sayfası için kod dosyasına kod ekleyin.

     kod dosyası, ASP.NET sayfa dosyası için düğümünü genişletirseniz ve projenin diline bağlı olarak *. cs* veya *. vb* uzantısına sahipse görüntülenir. uygulama sayfasının nasıl oluşturulacağını gösteren uçtan uca bir örnek için bkz. [izlenecek yol: SharePoint uygulama oluşturma sayfası](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [izlenecek yol: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
