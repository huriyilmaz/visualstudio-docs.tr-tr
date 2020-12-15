---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma'
description: Visual Studio 'Yu kullanarak bir Microsoft Excel çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla nasıl yazdırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523759"
---
# <a name="how-to-programmatically-print-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma

Çalışma kitabındaki tüm çalışma sayfalarını yazdırabilirsiniz.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasını yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfası yazdırmak için

1. Yöntemini çağırın `PrintOut` `Sheet1` , iki kopya isteyin ve yazdırmadan önce belgeyi önizleyin.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Yöntemi, belirtilen nesneyi **Baskı Önizleme** penceresinde görüntülemenizi sağlar. Aşağıdaki kod, <xref:Microsoft.Office.Tools.Excel.Worksheet> adlı bir konak öğesine sahip olduğunuzu varsayar `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Çalışma sayfasının yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma sayfasını yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfası yazdırmak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A>Etkin çalışma sayfasının yöntemini çağırın, iki kopya isteyin ve yazdırmadan önce belgeyi önizleyin.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Yöntemi, belirtilen nesneyi **Baskı Önizleme** penceresinde görüntülemenizi sağlar.

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Etkin çalışma sayfasının yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
