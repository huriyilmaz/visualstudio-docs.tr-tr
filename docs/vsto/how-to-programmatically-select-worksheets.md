---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6134b23e7b398794529ee43a428ee8b8962ccf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547010"
---
# <a name="how-to-programmatically-select-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>Yöntemi, kullanıcının seçimini yeni nesneye taşırken belirtilen nesneyi seçer. <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>Kullanıcının seçimini değiştirmeden nesneye odağı getirmek istiyorsanız yöntemini kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Bir VSTO eklentisinin içinde varolan bir çalışma sayfası seçmek istiyorsanız veya çalışma sayfası belge düzeyi özelleştirmesinde çalışma zamanında oluşturulduysa, <xref:Microsoft.Office.Interop.Excel.Sheets> Excel çalışma kitabının Excel koleksiyonunu kullanarak erişmeniz gerekir; Aksi takdirde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ana bilgisayar öğesine doğrudan erişebilirsiniz.

## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullan
 Belge düzeyi özelleştirmesinde, *Sheet1. vb* veya *Sheet1.cs*' ye aşağıdaki kodu ekleyin.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Bir konak öğesi kullanarak çalışma kitabındaki ilk çalışma sayfasını seçmek için

1. Yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanın
 Excel koleksiyonunu kullanarak çalışma sayfasına erişin <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanarak çalışma kitabındaki ilk çalışma sayfasını seçmek için

1. <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> <xref:Microsoft.Office.Interop.Excel.Sheets> Etkin çalışma kitabının ilk çalışma sayfasını seçmek için koleksiyonun yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma](../vsto/how-to-programmatically-print-worksheets.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
