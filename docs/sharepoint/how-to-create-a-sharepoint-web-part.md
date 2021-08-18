---
title: 'nasıl yapılır: SharePoint Web bölümü oluşturma | Microsoft Docs'
description: tasarımcı kullanarak bir web bölümü oluşturun ve özelleştirin veya bir web bölümü öğesini herhangi bir SharePoint projesine ekleyerek ve ardından web bölümü için kod dosyasını düzenleyerek.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ad3761012732f6191d40bfdf47da84221b78209e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130994"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>nasıl yapılır: SharePoint web bölümü oluşturma
  herhangi bir SharePoint projesine bir **web bölümü** öğesi ekleyerek ve sonra web bölümü için veya tasarımcı kullanarak bir web bölümü oluşturup özelleştirebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>SharePoint web bölümü oluşturmak için

1. bir SharePoint projesi oluşturun veya açın.

     daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini** SharePoint proje düğümünü seçin ve **Project**  >  **yeni öğe ekle**' yi seçin.

3. **yeni öğe ekle** iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. SharePoint şablonları listesinde, **Web bölümü**' nu seçin.

5. **Ad** kutusunda, Web bölümü için bir ad belirtin ve sonra **Ekle** düğmesini seçin.

     Web Bölümü **Çözüm Gezgini** görüntülenir. Bir Web bölümünün içerdiği dosyalar hakkında daha fazla bilgi için bkz. [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md).

6. **Çözüm Gezgini**' de, az önce oluşturduğunuz Web bölümü için kod dosyasını açın.

     örneğin, web bölümünün adı *WebPart1* ise, *WebPart1. vb* dosyasını açın (Visual Basic) veya *WebPart1. cs* (C# dilinde).

7. Kod dosyasında, yöntemine denetimler ekleyin <xref:System.Web.UI.Control.CreateChildControls%2A> .

     Bir örnek için bkz. [Izlenecek yol: SharePoint için Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [nasıl yapılır: tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [İzlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [izlenecek yol: tasarımcı kullanarak SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
