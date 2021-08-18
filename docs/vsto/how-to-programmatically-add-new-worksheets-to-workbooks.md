---
title: 'Nasıl yapılanlar: Çalışma kitaplarını program aracılığıyla yeni çalışma sayfalarına ekleme'
description: Program aracılığıyla çalışma sayfası oluşturma ve çalışma sayfasını çalışma kitabındaki çalışma sayfaları koleksiyonuna ekleme hakkında bilgi.
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
ms.openlocfilehash: 171608021bb967306a89e22bff68c7d3cd3ce639
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026258"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Nasıl yapılanlar: Çalışma kitaplarını program aracılığıyla yeni çalışma sayfalarına ekleme
  Program aracılığıyla bir çalışma sayfası oluşturabilir ve çalışma sayfasını çalışma kitabındaki çalışma sayfaları koleksiyonuna ekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede çalışma kitabına yeni çalışma sayfası eklemek için

1. Koleksiyonun <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> yöntemini <xref:Microsoft.Office.Interop.Excel.Sheets> kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet15":::

     Yeni çalışma sayfası bir konak öğesi <xref:Microsoft.Office.Interop.Excel.Worksheet> değil yerel bir nesnedir. Konak öğesi eklemek için <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma sayfasını tasarım zamanında eklemeniz gerekir.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Bir çalışma kitabındaki çalışma kitabına yeni bir çalışma sayfası VSTO eklemek için

1. Koleksiyonun <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> yöntemini <xref:Microsoft.Office.Interop.Excel.Sheets> kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet11":::

     Yeni çalışma sayfası bir konak öğesi <xref:Microsoft.Office.Interop.Excel.Worksheet> değil yerel bir nesnedir. Ayrıca yerel nesneden <xref:Microsoft.Office.Tools.Excel.Worksheet> bir konak öğesi de <xref:Microsoft.Office.Interop.Excel.Worksheet> oluşturabilirsiniz. Daha fazla bilgi için bkz. Çalışma Zamanında Excel Eklentilerini VSTO Çalışma [Kitaplarını Genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılanlar: Çalışma kitaplarından program aracılığıyla çalışma sayfalarını silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını seçme](../vsto/how-to-programmatically-select-worksheets.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
