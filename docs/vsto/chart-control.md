---
title: Grafik denetimi
description: Çalışma sayfasına bir grafik eklediğinizde, Visual Studio 'Nun doğrudan programlayabilirsiniz bir grafik nesnesi oluşturduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3530e0821d4569381f610f44ae541c04b484b469
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903783"
---
# <a name="chart-control"></a>Grafik denetimi
  <xref:Microsoft.Office.Tools.Excel.Chart>Denetim, olayları ortaya çıkaran bir grafik nesnesidir. Bir çalışma sayfasına bir grafik eklediğinizde, Visual Studio <xref:Microsoft.Office.Tools.Excel.Chart> Microsoft Office Excel nesne modelinde geçiş yapmak zorunda kalmadan doğrudan programlama yapabileceğiniz bir nesne oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetim oluşturma
 <xref:Microsoft.Office.Tools.Excel.Chart>Tasarım zamanında Microsoft Office Excel çalışma sayfasına veya belge düzeyindeki bir projede çalışma zamanında denetimler ekleyebilirsiniz.

 <xref:Microsoft.Office.Tools.Excel.Chart>Bir çalışma sayfasına BIR VSTO eklentisinin çalışma zamanında denetim ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafik denetimlerini çalışma sayfalarına ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Çalışma sayfası kapatıldığında dinamik olarak oluşturulan grafik nesneleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="formatting"></a>Biçimlendirme
 Bir denetimine uygulanabilecek tüm biçimlendirmeler <xref:Microsoft.Office.Interop.Excel.Chart> de bir <xref:Microsoft.Office.Tools.Excel.Chart> denetime uygulanabilir. Bu, kenarlıkları, yazı tiplerini, grafik türünü, kılavuz çizgilerini, göstergeyi ve veri etiketlerini içerir.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar mevcuttur <xref:Microsoft.Office.Tools.Excel.Chart> :

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Ayrıca bkz.
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
