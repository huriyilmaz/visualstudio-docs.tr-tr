---
title: Office uygulama ve proje türü tarafından kullanılabilen özellikler
description: Visual Studio, Microsoft Office uygulamalar için farklı iş senaryolarını destekleyen çeşitli proje şablonu türlerine sahip olduğunu öğrenin.
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
ms.openlocfilehash: bb532244198a26da0106652f3c1167ef111c91ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106360"
---
# <a name="features-available-by-office-application-and-project-type"></a>Office uygulama ve proje türü tarafından kullanılabilen özellikler
  Visual Studio, aşağıdaki türler dahil olmak üzere Microsoft Office uygulamalar için farklı iş senaryolarını destekleyen çeşitli proje şablonu türlerine sahiptir:

- Belge düzeyi özelleştirmeleri.

- VSTO Eklentiler.

  Tüm uygulamalar her proje türünü kullanamaz. örneğin, belge düzeyi projeler yalnızca Microsoft Office sözcük ve Microsoft Office Excel için kullanılabilir. Benzer şekilde, bazı özellikler yalnızca belirli proje veya uygulama türleri için kullanılabilir. Örneğin, Eylemler bölmesi yalnızca belge düzeyi projelerde kullanılabilir ve Şerit uzantıları yalnızca bazı uygulamalar için kullanılabilir. farklı proje türleri hakkında daha fazla bilgi için, bkz. [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Office proje şablonları yalnızca bazı sürümlerinde kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>farklı Microsoft Office uygulamalar için kullanılabilir Project türleri
 Aşağıdaki tabloda her proje türüyle kullanabileceğiniz uygulamalar gösterilmektedir.

|Project türleri|Microsoft Office uygulaması|
|-------------------|----------------------------------|
|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|
|VSTO Eklentiler|Excel<br /><br /> InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Farklı proje türlerinde kullanılabilen özellikler
 Aşağıdaki tabloda her bir özelliği hangi proje türlerinin sağladığı gösterilmektedir.

|Özellik|özelliği sağlayan Project türleri|Daha fazla bilgi|
|-------------|--------------------------------------------|---------------------|
|Eylemler bölmesi.|Belge düzeyi projeler.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)|
|ClickOnce dağıtımı.|VS ve belge düzeyindeki projeler.|[Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)|
|Özel görev bölmeleri.|VSTO Aşağıdaki uygulamalar için eklenti projeleri:<br /><br /> -Excel<br />-InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Sözcük|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|
|Özel XML bölümleri.|Belge düzeyi projeler.<br /><br /> Aşağıdaki uygulamalar için uygulama düzeyi projeleri:<br /><br /> -Excel<br />-PowerPoint<br />-Sözcük|[Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)|
|Veri önbelleği.|Belge düzeyi projeler.|[Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)|
|VSTO eklenti içindeki bir nesneyi diğer Microsoft Office çözümlerine sunun.|VSTO Eklenti projeleri.|[diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Aşağıdaki konak denetimleri:<br /><br /> -Grafik<br />-ListObject<br />-NamedRange<br />-İçerik denetimleri<br />-Yer işareti|Belge düzeyi projeler.<br /><br /> VSTO Word ve Excel için eklenti projeleri.|[Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Aşağıdaki konak denetimleri:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Belge düzeyi projeler.|[Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Çoklu proje dağıtımı.|Belge düzeyi projeler.<br /><br /> VSTO Eklenti projeleri.|[izlenecek yol: tek bir ClickOnce yükleyicide birden çok Office çözümü dağıtma](/previous-versions/dd465290(v=vs.110))|
|Outlook form bölgeleri.|VSTO Outlook için eklenti projeleri.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|
|Dağıtım sonrası eylemleri.|Belge düzeyi projeler.<br /><br /> VSTO Eklenti projeleri.|[izlenecek yol: ClickOnce yüklemesinden sonra bir belgeyi son kullanıcı bilgisayarına kopyalama](/previous-versions/dd465291(v=vs.110))|
|Şerit özelleştirmeleri.|Belge düzeyi projeler.<br /><br /> VSTO Aşağıdaki uygulamalar için eklenti projeleri:<br /><br /> -Excel<br />-InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Project<br />-Visio<br />-Sözcük|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|Görsel belge Tasarımcısı.|Belge düzeyi projeler.|[Visual Studio ortamındaki projeleri Office](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)