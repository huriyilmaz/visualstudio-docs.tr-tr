---
title: Grafik denetimi
description: bir çalışma sayfasına grafik eklediğinizde Visual Studio doğrudan programlayabilirsiniz bir grafik nesnesi oluşturduğunu öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cd48c96ba1980a6c95207fae9674ad5480aa961f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726719"
---
# <a name="chart-control"></a>Grafik denetimi
  <xref:Microsoft.Office.Tools.Excel.Chart>Denetim, olayları ortaya çıkaran bir grafik nesnesidir. bir çalışma sayfasına bir grafik eklediğinizde Visual Studio, <xref:Microsoft.Office.Tools.Excel.Chart> Microsoft Office Excel nesne modelinde geçiş yapmak zorunda kalmadan doğrudan programlama yapabileceğiniz bir nesne oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetim oluşturma
 bir <xref:Microsoft.Office.Tools.Excel.Chart> Microsoft Office Excel çalışma sayfasına tasarım zamanında veya belge düzeyindeki bir projede çalışma zamanında denetim ekleyebilirsiniz.

 <xref:Microsoft.Office.Tools.Excel.Chart>çalışma zamanında bir VSTO eklentisinin çalışma sayfasına denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafik denetimlerini çalışma sayfalarına ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Çalışma sayfası kapatıldığında dinamik olarak oluşturulan grafik nesneleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

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
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
