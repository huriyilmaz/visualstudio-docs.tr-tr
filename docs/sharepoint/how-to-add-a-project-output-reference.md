---
title: 'nasıl yapılır: Project çıkış başvurusu ekleme | Microsoft Docs'
description: SharePoint için SharePoint olmayan proje derlemelerini (veya Silverlight projelerinde. xap dosyaları) dağıtabilmeniz için bir proje çıkış başvurusu eklemeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d3d7bea0d57e4351fc022b2f4c45ecc1b6423e4b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060121"
---
# <a name="how-to-add-a-project-output-reference"></a>Nasıl yapılır: proje çıktı başvurusu ekleme
  SharePoint için SharePoint olmayan proje derlemelerini (veya. xap dosyalarını Silverlight projelerinde) dağıtmak için, bunları bir proje çıktı başvurusu olarak ekleyin.

 Bu işlem iki proje arasında bir çözüm derleme bağımlılığı oluşturur. proje çıkış başvurularıyla ilişkili projeler, SharePoint projesi oluşturulup dağıtılmadan önce oluşturulur.

### <a name="to-add-a-project-output-reference"></a>Proje çıkış başvurusu eklemek için

1. en az bir SharePoint projesi ve SharePoint olmayan bir proje içeren bir çözüm yükleyin.

2. **Çözüm Gezgini**, SharePoint projesi düğümünde bir öğe seçin.

3. **özellikler** penceresinde, **çıkış başvuruları özelliğini Project** seçin ve yanındaki üç nokta (![ASP.NET Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) düğmesini seçin.

4. **çıkış başvurularını Project** iletişim kutusunda **ekle** düğmesini seçin.

5. özellikler bölmesinde, **dağıtım türü** özelliğinin yanındaki oku seçin ve ardından başvuru yaptığınız SharePoint olmayan öğe için **elementfile** gibi uygun bir değer seçin.

6. **Project ad**' ın yanındaki oku seçin, SharePoint olmayan proje öğesinin adını seçin ve **tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Nasıl yapılır: denetimleri güvenli denetim olarak Işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
