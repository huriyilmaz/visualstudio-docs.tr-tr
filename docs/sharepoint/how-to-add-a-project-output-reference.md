---
title: 'Nasıl Project: Project Çıkış Başvurusu | Microsoft Docs'
description: SharePoint olmayan proje derlemelerini (veya Silverlight projelerinde .xap dosyalarını) dağıtıma dağıtmak için bir proje çıkış başvurusu SharePoint.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625154"
---
# <a name="how-to-add-a-project-output-reference"></a>Nasıl: Proje çıkış başvurusu ekleme
  SharePoint olmayan proje derlemelerini (veya Silverlight projelerinde .xap dosyaları) SharePoint proje çıkış başvurusu olarak ekleyin.

 Bu işlem, iki proje arasında bir çözüm derleme bağımlılığı oluşturur. Proje çıkış başvuruları ile ilişkilendirilmiş projeler, proje SharePoint ve dağıtıldıktan önce hazırlar.

### <a name="to-add-a-project-output-reference"></a>Proje çıkış başvurusu eklemek için

1. En az bir proje ve bir SharePoint olmayan proje içeren bir SharePoint yükleme.

2. Bu **Çözüm Gezgini** proje düğümünde bir SharePoint seçin.

3. Özellikler **penceresinde,** **Project** Çıkış Başvuruları özelliğini seçin ve ardından yanındaki üç noktayı (![ASP.NET Mobil](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")Tasarımcı üç nokta ) düğmesini seçin.

4. Çıkış **Project iletişim** kutusunda Ekle **düğmesini** seçin.

5. Özellikler bölmesinde, Dağıtım Türü özelliğinin  yanındaki oku seçin ve ardından başvurdurma dışı öğe için uygun SharePoint uygun bir değer seçin, **örneğin, ElementFile**.

6. Ad'Project **yanındaki oku** seçin, SharePoint olmayan proje öğesinin adını seçin ve ardından Tamam **düğmesini** seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Nasıllı: Denetimleri güvenli denetimler olarak işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Çözümlerini paket SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
