---
title: 'Nasıl yapılır: proje çıktı başvurusu ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016748"
---
# <a name="how-to-add-a-project-output-reference"></a>Nasıl yapılır: proje çıktı başvurusu ekleme
  SharePoint olmayan proje derlemelerini (veya. xap dosyalarını Silverlight projelerinde) SharePoint 'e dağıtmak için, bunları bir proje çıktı başvurusu olarak ekleyin.

 Bu işlem iki proje arasında bir çözüm derleme bağımlılığı oluşturur. Proje çıkış başvurularıyla ilişkili projeler, SharePoint projesi oluşturulup dağıtılmadan önce oluşturulur.

### <a name="to-add-a-project-output-reference"></a>Proje çıkış başvurusu eklemek için

1. En az bir SharePoint projesi ve SharePoint olmayan bir proje içeren bir çözüm yükleyin.

2. **Çözüm Gezgini**, SharePoint proje düğümünde bir öğe seçin.

3. **Özellikler** penceresinde, **Proje çıktısı başvuruları** özelliğini seçin ve yanındaki üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

4. **Proje çıktısı başvuruları** Iletişim kutusunda **Ekle** düğmesini seçin.

5. Özellikler bölmesinde, **dağıtım türü** özelliğinin yanındaki oku seçin ve ardından başvuru yaptığınız SharePoint olmayan öğe Için **ElementFile**gibi uygun bir değer seçin.

6. **Proje adı**' nın yanındaki oku seçin, SharePoint olmayan proje öğesinin adını seçin ve **Tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Nasıl yapılır: denetimleri güvenli denetim olarak Işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
