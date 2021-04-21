---
title: 'Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme'
description: Tasarım zamanında Microsoft Office Excel çalışma sayfasına ve belge düzeyi özelleştirmelerde çalışma zamanında grafik denetimleri nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88ebe38a881e148f10149189a2d27ac81bd0ddc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827038"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme
  <xref:Microsoft.Office.Tools.Excel.Chart>Tasarım zamanında Microsoft Office Excel çalışma sayfasına ve belge düzeyi özelleştirmelerde çalışma zamanında denetim ekleyebilirsiniz. Ayrıca, <xref:Microsoft.Office.Tools.Excel.Chart> VSTO Eklentilerindeki çalışma zamanında denetim ekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında grafik denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında grafik denetimleri ekleme](#runtimedoclevel)

- [VSTO eklenti projesindeki çalışma zamanında grafik denetimleri ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.Chart> bkz. [Chart Control](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında grafik denetimleri ekleme
 Denetim sayfanıza, <xref:Microsoft.Office.Tools.Excel.Chart> uygulamanın içinden bir grafik ekleyeceğiniz şekilde ekleyebilirsiniz.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.Chart>Denetim, **araç kutusu** veya **veri kaynakları** penceresinde kullanılamaz.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Excel 'deki çalışma sayfasına bir grafik konak denetimi eklemek için

1. **Ekle** sekmesinde, **grafikler** grubunda, **sütun**' a tıklayın, bir grafik kategorisine tıklayın ve sonra istediğiniz grafik türüne tıklayın.

2. **Grafik Ekle** Iletişim kutusunda **Tamam**' a tıklayın.

3. **Tasarım** sekmesinde, **veri** grubunda, **veri Seç**' e tıklayın.

4. **Veri kaynağı seç** iletişim kutusunda, **grafik** **veri aralığı** kutusuna tıklayın ve varsayılan seçimi kaldırın.

5. **Grafik verileri** sayfasında, grafiğe ait verileri içeren hücre aralığını seçin ( **a5** - **D8** arası hücreler).

6. **Veri kaynağı seç** Iletişim kutusunda **Tamam**' a tıklayın.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında grafik denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.Chart>Denetimi çalışma zamanında dinamik olarak ekleyebilirsiniz. Belge kapatıldığında dinamik olarak oluşturulan grafikler, belgede konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir şekilde grafik denetimi eklemek için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>Olay işleyicisinde `Sheet1` , denetimi eklemek için aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Excel.Chart> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> VSTO eklenti projesindeki çalışma zamanında grafik denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.Chart>VSTO eklenti projesindeki herhangi bir açık çalışma sayfasına programlı olarak bir denetim ekleyebilirsiniz. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Çalışma sayfası kapatıldığında dinamik olarak oluşturulan grafik denetimleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir şekilde grafik denetimi eklemek için

1. Aşağıdaki kod, açık çalışma sayfasına dayalı bir çalışma sayfası konak öğesi oluşturur ve sonra bir <xref:Microsoft.Office.Tools.Excel.Chart> denetim ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek aşağıdaki gereksinimlere sahiptir:

- Çalışma sayfasındaki a5 ile D8 arasında depolanan, grafiklenen veriler.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Grafik denetimi](../vsto/chart-control.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
