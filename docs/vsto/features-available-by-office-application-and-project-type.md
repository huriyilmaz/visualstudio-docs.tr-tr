---
title: Office uygulaması ve proje türü tarafından kullanılabilen özellikler
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24344a643e9ec2b4a7bb90dc62df67209b3eb183
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808187"
---
# <a name="features-available-by-office-application-and-project-type"></a>Office uygulaması ve proje türü tarafından kullanılabilen özellikler
  Visual Studio, aşağıdaki türler dahil olmak üzere Microsoft Office uygulamalar için farklı iş senaryolarını destekleyen çeşitli proje şablonu türlerine sahiptir:

- Belge düzeyi özelleştirmeleri.

- VSTO eklentileri.

  Tüm uygulamalar her proje türünü kullanamaz. Örneğin, belge düzeyi projeler yalnızca Microsoft Office Word ve Excel Microsoft Office için kullanılabilir. Benzer şekilde, bazı özellikler yalnızca belirli proje veya uygulama türleri için kullanılabilir. Örneğin, Eylemler bölmesi yalnızca belge düzeyi projelerde kullanılabilir ve Şerit uzantıları yalnızca bazı uygulamalar için kullanılabilir. Farklı proje türleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Office proje şablonları yalnızca bazı sürümlerinde kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Farklı Microsoft Office uygulamalar için kullanılabilir proje türleri
 Aşağıdaki tabloda her proje türüyle kullanabileceğiniz uygulamalar gösterilmektedir.

|Proje türleri|Microsoft Office uygulaması|
|-------------------|----------------------------------|
|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|
|VSTO eklentileri|Excel<br /><br /> InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Farklı proje türlerinde kullanılabilen özellikler
 Aşağıdaki tabloda her bir özelliği hangi proje türlerinin sağladığı gösterilmektedir.

|Öne çıkan özelliği|Özelliği sağlayan proje türleri|Daha fazla bilgi|
|-------------|--------------------------------------------|---------------------|
|Eylemler bölmesi.|Belge düzeyi projeler.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)|
|ClickOnce dağıtımı.|VS ve belge düzeyindeki projeler.|[Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)|
|Özel görev bölmeleri.|Aşağıdaki uygulamalar için VSTO eklentisi projeleri:<br /><br /> -Excel<br />-InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Sözcük|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|
|Özel XML bölümleri.|Belge düzeyi projeler.<br /><br /> Aşağıdaki uygulamalar için uygulama düzeyi projeleri:<br /><br /> -Excel<br />-PowerPoint<br />-Sözcük|[Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)|
|Veri önbelleği.|Belge düzeyi projeler.|[Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)|
|VSTO Eklentilerindeki bir nesneyi diğer Microsoft Office çözümlerine sunun.|VSTO eklenti projeleri.|[Diğer Office çözümlerindeki VSTO eklentilerindeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Aşağıdaki konak denetimleri:<br /><br /> -Grafik<br />-ListObject<br />-NamedRange<br />-İçerik denetimleri<br />-Yer işareti|Belge düzeyi projeler.<br /><br /> Word ve Excel için VSTO eklentisi projeleri.|[Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Aşağıdaki konak denetimleri:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Belge düzeyi projeler.|[Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|
|Çoklu proje dağıtımı.|Belge düzeyi projeler.<br /><br /> VSTO eklenti projeleri.|[İzlenecek yol: tek bir ClickOnce Yükleyicisinde birden çok Office çözümünü dağıtma](/previous-versions/dd465290(v=vs.110))|
|Outlook form bölgeleri.|Outlook için VSTO eklenti projeleri.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|
|Dağıtım sonrası eylemleri.|Belge düzeyi projeler.<br /><br /> VSTO eklenti projeleri.|[İzlenecek yol: ClickOnce yüklemesinden sonra bir belgeyi son kullanıcı bilgisayarına kopyalama](/previous-versions/dd465291(v=vs.110))|
|Şerit özelleştirmeleri.|Belge düzeyi projeler.<br /><br /> Aşağıdaki uygulamalar için VSTO eklentisi projeleri:<br /><br /> -Excel<br />-InfoPath (yalnızca InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Proje<br />-Visio<br />-Sözcük|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|Görsel belge Tasarımcısı.|Belge düzeyi projeler.|[Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Belge düzeyi Özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)