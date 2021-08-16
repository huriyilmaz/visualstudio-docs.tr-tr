---
title: 'Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını yazdırma'
description: Çalışma kitabındaki herhangi bir çalışma Visual Studio program aracılığıyla yazdırmak için Microsoft Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9671e678c28523bf3ab0aaeb443845b795f7b208b9db5db459afcd2692a08e7d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440740"
---
# <a name="how-to-programmatically-print-worksheets"></a>Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını yazdırma

Çalışma kitabındaki herhangi bir çalışma sayfasını yazdırabilirsiniz.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede çalışma sayfası yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfasını yazdırmak için

1. yöntemini `PrintOut` çağırarak `Sheet1` iki kopya isteğinde bulundurabilirsiniz ve yazdırmadan önce belgenin önizlemesini görebilirsiniz.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   yöntemi, <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> belirtilen nesneyi Baskı Önizleme penceresinde **görüntülemeye olanak** sağlar. Aşağıdaki kod, adlı bir konak <xref:Microsoft.Office.Tools.Excel.Worksheet> öğeye sahip olduğunu varsayıyor. `Sheet1`

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. Çalışma <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> sayfasının yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Çalışma sayfasını VSTO yazdırma

### <a name="to-print-a-worksheet"></a>Çalışma sayfasını yazdırmak için

1. Etkin çalışma <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> sayfasının yöntemini çağırarak iki kopya isteğinde bulundurabilirsiniz ve yazdırmadan önce belgenin önizlemesini görebilirsiniz.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   yöntemi, <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> belirtilen nesneyi Baskı Önizleme penceresinde **görüntülemeye olanak** sağlar.

### <a name="to-preview-a-page-before-printing"></a>Yazdırmadan önce bir sayfayı önizlemek için

1. Etkin <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> çalışma sayfasının yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıllı: Çalışma sayfasında program aracılığıyla yazım denetimi yapma](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
