---
title: Uygulama ve Office tarafından kullanılabilen özellikler
description: Uygulama Visual Studio için farklı iş senaryolarını destekleyen çeşitli türde proje şablonlarının nasıl Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 42e816a19a52e2da3a1cd123b88577c20abff6f4d21c85a228f545e2591fe725
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352103"
---
# <a name="features-available-by-office-application-and-project-type"></a>Uygulama ve Office tarafından kullanılabilen özellikler
  Visual Studio uygulamaları için farklı iş senaryolarını destekleyen çeşitli proje şablonları Microsoft Office türleri de vardır:

- Belge düzeyinde özelleştirmeler.

- VSTO Eklentiler.

  Tüm uygulamalar her proje türünü kullanamayabilirsiniz. Örneğin, belge düzeyi projeler yalnızca Word ve Microsoft Office için Microsoft Office Excel. Benzer şekilde, bazı özellikler yalnızca belirli proje veya uygulama türleri için kullanılabilir. Örneğin, eylemler bölmesi yalnızca belge düzeyi projelerde kullanılabilir ve Şerit uzantıları yalnızca bazı uygulamalar için kullanılabilir. Farklı proje türleri hakkında daha fazla bilgi için bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

> [!NOTE]
> Office şablonları yalnızca bazı sürümlerinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanılabilir. Daha fazla bilgi için, [bkz. Configure a computer to develop Office .](../vsto/configuring-a-computer-to-develop-office-solutions.md)

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Project uygulama için kullanılabilen Microsoft Office türleri
 Aşağıdaki tabloda, her proje türüyle birlikte kullanabileceğiniz uygulamalar yer alır.

|Project türleri|Microsoft Office uygulama|
|-------------------|----------------------------------|
|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|
|VSTO Eklentiler|Excel<br /><br /> InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Farklı proje türlerinde kullanılabilen özellikler
 Aşağıdaki tabloda, her bir özelliği hangi proje türleri sağlar?

|Özellik|Project sağlayan türler|Daha fazla bilgi|
|-------------|--------------------------------------------|---------------------|
|Eylemler bölmesi.|Belge düzeyi projeler.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)|
|ClickOnce dağıtım.|VS ve belge düzeyi projeler.|[Bir Office dağıtma](../vsto/deploying-an-office-solution.md)|
|Özel görev bölmeleri.|VSTO Aşağıdaki uygulamalar için eklenti projeleri:<br /><br /> - Excel<br />- InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />- Outlook<br />- PowerPoint<br />- Word|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|
|Özel XML bölümleri.|Belge düzeyi projeler.<br /><br /> Aşağıdaki uygulamalar için uygulama düzeyi projeler:<br /><br /> - Excel<br />- PowerPoint<br />- Word|[Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)|
|Veri önbelleği.|Belge düzeyi projeler.|[Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)|
|Bir nesne bir eklentide VSTO diğer çözümlerde Microsoft Office.|VSTO Eklenti projeleri.|[Diğer VSTO çözümlerinden eklentilerde kod Office çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Aşağıdaki konak denetimleri:<br /><br /> - Grafik<br />- ListObject<br />- NamedRange<br />- İçerik denetimleri<br />- Yer işareti|Belge düzeyi projeler.<br /><br /> VSTO Word ve Excel için eklenti projeleri.|[Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Aşağıdaki konak denetimleri:<br /><br /> - XMLMappedRange<br />- XMLNode<br />- XMLNodes|Belge düzeyi projeler.|[Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Çoklu proje dağıtımı.|Belge düzeyi projeler.<br /><br /> VSTO Eklenti projeleri.|[Adım adım kılavuz: Tek Office birden fazla çözüm ClickOnce dağıtma](/previous-versions/dd465290(v=vs.110))|
|Outlook bölgeleri seçin.|VSTO Outlook için Outlook.|[Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|
|Dağıtım sonrası eylemler.|Belge düzeyi projeler.<br /><br /> VSTO Eklenti projeleri.|[Adım adım kılavuz: Bir belgeyi bir belgeyi bir yüklemeden sonra son ClickOnce kopyalama](/previous-versions/dd465291(v=vs.110))|
|Şerit özelleştirmeleri.|Belge düzeyi projeler.<br /><br /> VSTO Aşağıdaki uygulamalar için eklenti projeleri:<br /><br /> - Excel<br />- InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />- Outlook<br />- PowerPoint<br />- Project<br />- Visio<br />- Word|[Şerit'e genel bakış](../vsto/ribbon-overview.md)|
|Görsel belge tasarımcısı.|Belge düzeyi projeler.|[Office ortamında Visual Studio projeleri](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümlerine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)