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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827155"
---
# <a name="how-to-programmatically-print-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma

Çalışma kitabındaki tüm çalışma sayfalarını yazdırabilirsiniz.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasını yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfası yazdırmak için

1. Yöntemini çağırın `PrintOut` `Sheet1` , iki kopya isteyin ve yazdırmadan önce belgeyi önizleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Yöntemi, belirtilen nesneyi **Baskı Önizleme** penceresinde görüntülemenizi sağlar. Aşağıdaki kod, <xref:Microsoft.Office.Tools.Excel.Worksheet> adlı bir konak öğesine sahip olduğunuzu varsayar `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma sayfasını yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfası yazdırmak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A>Etkin çalışma sayfasının yöntemini çağırın, iki kopya isteyin ve yazdırmadan önce belgeyi önizleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Yöntemi, belirtilen nesneyi **Baskı Önizleme** penceresinde görüntülemenizi sağlar.

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Etkin çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
