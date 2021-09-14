---
title: 'Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını seçme'
description: Çalışma Visual Studio çalışma sayfası konak öğesi Microsoft Excel çalışma kitabının sayfa koleksiyonuyla program aracılığıyla seçim yapmak için Excel kullanın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726711"
---
# <a name="how-to-programmatically-select-worksheets"></a>Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını seçme
  yöntemi, <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> kullanıcının seçimini yeni nesneye taşır ve belirtilen nesneyi seçer. Kullanıcının <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> seçimini değiştirmeden odağı nesneye getirmek için yöntemini kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 VSTO Eklentisinde var olan bir çalışma sayfasını seçmek veya çalışma sayfası belge düzeyi özelleştirmede çalışma zamanında oluşturulduysa, Excel çalışma kitabının Excel koleksiyonunu kullanarak bu çalışma sayfasına erişmeniz gerekir; aksi takdirde konak öğeye doğrudan <xref:Microsoft.Office.Interop.Excel.Sheets> <xref:Microsoft.Office.Tools.Excel.Worksheet> erişebilirsiniz.

## <a name="use-the-worksheet-host-item"></a>Çalışma sayfası konak öğesini kullanma
 Belge düzeyinde özelleştirmede, aşağıdaki kodu *Sheet1.vb* veya *Sheet1.cs'ye ekleyin.*

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Konak öğesi kullanarak çalışma kitabındaki ilk çalışma sayfasını seçmek için

1. yöntemini <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> `Sheet1` çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Çalışma kitabının sayfa koleksiyonunu Excel kullanma
 Çalışma sayfasına erişmek için Excel <xref:Microsoft.Office.Interop.Excel.Sheets> erişin.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Çalışma kitabının Sayfa koleksiyonunu kullanarak çalışma kitabındaki ilk çalışma sayfasını Excel için

1. Etkin <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> çalışma kitabının <xref:Microsoft.Office.Interop.Excel.Sheets> ilk çalışma sayfasını seçmek için koleksiyonun yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıllı: Program aracılığıyla çalışma sayfalarını yazdırma](../vsto/how-to-programmatically-print-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarından program aracılığıyla çalışma sayfalarını silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
