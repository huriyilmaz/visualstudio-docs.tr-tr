---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme'
description: çalışma sayfası konak öğesi veya Excel çalışma kitabının sayfalar koleksiyonuyla Microsoft Excel çalışma sayfalarını program aracılığıyla seçmek için Visual Studio kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 82d74fff713741208981278474b295c17975a639
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032738"
---
# <a name="how-to-programmatically-select-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>Yöntemi, kullanıcının seçimini yeni nesneye taşırken belirtilen nesneyi seçer. <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>Kullanıcının seçimini değiştirmeden nesneye odağı getirmek istiyorsanız yöntemini kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 bir VSTO eklentisi içinde var olan bir çalışma sayfası seçmek istiyorsanız veya çalışma sayfası bir belge düzeyi özelleştirmesindeki çalışma zamanında oluşturulduysa, Excel çalışma kitabının Excel koleksiyonunu kullanarak buna erişmeniz gerekir <xref:Microsoft.Office.Interop.Excel.Sheets> ; aksi takdirde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ana bilgisayar öğesine doğrudan erişebilirsiniz.

## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullan
 Belge düzeyi özelleştirmesinde, *Sheet1. vb* veya *Sayfa1. cs*' ye aşağıdaki kodu ekleyin.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Bir konak öğesi kullanarak çalışma kitabındaki ilk çalışma sayfasını seçmek için

1. Yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanın
 Excel koleksiyonunu kullanarak çalışma sayfasına erişin <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel çalışma kitabının sayfalar koleksiyonunu kullanarak çalışma kitabındaki ilk çalışma sayfasını seçmek için

1. <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> <xref:Microsoft.Office.Interop.Excel.Sheets> Etkin çalışma kitabının ilk çalışma sayfasını seçmek için koleksiyonun yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma](../vsto/how-to-programmatically-print-worksheets.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
