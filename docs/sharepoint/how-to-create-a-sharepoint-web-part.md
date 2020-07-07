---
title: 'Nasıl yapılır: SharePoint Web Bölümü oluşturma | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a8c02cce2f55374b4d62ba5663e8b3fe85b55b5
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016436"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Nasıl yapılır: SharePoint Web Bölümü oluşturma
  Herhangi bir SharePoint projesine **Web** bölümü öğesi ekleyerek ve sonra Web bölümü için veya Tasarımcı kullanarak bir Web bölümü oluşturup özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>SharePoint Web bölümü oluşturmak için

1. Bir SharePoint projesi oluşturun veya açın.

     Daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini** ' de SharePoint projesi düğümünü seçin ve ardından **Proje**  >  **Yeni öğe Ekle**' yi seçin.

3. **Yeni öğe Ekle** iletişim kutusunda, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. SharePoint şablonları listesinde, **Web Bölümü**' nu seçin.

5. **Ad** kutusunda, Web bölümü için bir ad belirtin ve sonra **Ekle** düğmesini seçin.

     Web Bölümü **Çözüm Gezgini**görüntülenir. Bir Web bölümünün içerdiği dosyalar hakkında daha fazla bilgi için bkz. [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md).

6. **Çözüm Gezgini**' de, az önce oluşturduğunuz Web bölümü için kod dosyasını açın.

     Örneğin, Web bölümünün adı *WebPart1*Ise, *WebPart1. vb* dosyasını açın (Visual Basic) veya *WebPart1.cs* (C# dilinde).

7. Kod dosyasında, yöntemine denetimler ekleyin <xref:System.Web.UI.Control.CreateChildControls%2A> .

     Bir örnek için bkz. [Izlenecek yol: SharePoint için Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Nasıl yapılır: tasarımcı kullanarak SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [İzlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [İzlenecek yol: tasarımcı kullanarak SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
