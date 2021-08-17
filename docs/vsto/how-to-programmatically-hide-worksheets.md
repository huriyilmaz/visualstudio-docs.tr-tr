---
title: 'Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla gizleme'
description: Çalışma sayfası konak öğesini kullanarak program aracılığıyla bir çalışma kitabındaki çalışma Microsoft Excel göstermeyi veya gizlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: bac632610319a5e73cece299357c80160155eaa2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106074"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla gizleme
  Çalışma kitabındaki çalışma sayfalarını gösterebilir veya gizleyebilirsiniz. Bir çalışma sayfasını gizlemek için çalışma sayfası konak öğesini kullanın veya çalışma kitabının sayfa koleksiyonunu kullanarak çalışma sayfasına erişin.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullanma
 Çalışma sayfası tasarım zamanında belge düzeyi özelleştirmeyle eklendiyse, belirtilen çalışma <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> sayfasını gizlemek için özelliğini kullanın.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullanarak çalışma sayfasını gizlemek için

1. Konak <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> `Sheet1` öğesinin özelliğini, <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> numaralama değerine ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet25":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Çalışma kitabının Sayfa koleksiyonunu Excel kullanma
 Aşağıdaki durumlarda çalışma sayfalarına Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyonu aracılığıyla erişin:

- Çalışma sayfasını Bir Çalışma Sayfası VSTO gizlemek istediğiniz.

- Gizlemek istediğiniz çalışma sayfası çalışma zamanında belge düzeyinde özelleştirmeyle oluşturulmuş.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Çalışma kitabının Sayfa koleksiyonunu kullanarak çalışma sayfasını Excel için

1. Çalışma <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> sayfasının özelliğini <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> numaralama değerine ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet26":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarından program aracılığıyla çalışma sayfalarını silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl olur: Çalışma kitaplarında program aracılığıyla çalışma sayfalarını taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
