---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme'
description: Programlı olarak bir çalışma sayfası oluşturma ve çalışma kitabını çalışma kitabındaki çalışma sayfaları koleksiyonuna ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1f3d84e5c16bd6961428552d96468cd46e4049886d85e798f29ab3cbe1362a2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384385"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme
  Programlı olarak bir çalışma sayfası oluşturabilir ve çalışma kitabını çalışma kitabındaki çalışma sayfaları koleksiyonuna ekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma kitabına yeni bir çalışma sayfası eklemek için

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>Koleksiyonun yöntemini kullanın <xref:Microsoft.Office.Interop.Excel.Sheets> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet15":::

     Yeni çalışma sayfası, <xref:Microsoft.Office.Interop.Excel.Worksheet> konak öğesi değil, yerel bir nesnedir. Bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi eklemek istiyorsanız, çalışma sayfasını Tasarım zamanında eklemeniz gerekir.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>VSTO eklentisi içindeki çalışma kitabına yeni bir çalışma sayfası eklemek için

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>Koleksiyonun yöntemini kullanın <xref:Microsoft.Office.Interop.Excel.Sheets> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet11":::

     Yeni çalışma sayfası, <xref:Microsoft.Office.Interop.Excel.Worksheet> konak öğesi değil, yerel bir nesnedir. <xref:Microsoft.Office.Tools.Excel.Worksheet>Yerel nesneden bir konak öğesi de oluşturabilirsiniz <xref:Microsoft.Office.Interop.Excel.Worksheet> . daha fazla bilgi için bkz. [çalışma zamanında Word belgelerini ve Excel çalışma kitaplarını VSTO eklentilerinde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme](../vsto/how-to-programmatically-select-worksheets.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
