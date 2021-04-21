---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme'
description: Çalışma sayfası konak öğesi veya Excel çalışma kitabının sayfalar koleksiyonuyla Microsoft Excel çalışma sayfalarını programlı bir şekilde seçmek için Visual Studio 'Yu kullanın.
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
ms.workload:
- office
ms.openlocfilehash: 04f410292fff686e7604e917e6c3fa7002c65273
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826258"
---
# <a name="how-to-programmatically-select-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>Yöntemi, kullanıcının seçimini yeni nesneye taşırken belirtilen nesneyi seçer. <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>Kullanıcının seçimini değiştirmeden nesneye odağı getirmek istiyorsanız yöntemini kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Bir VSTO eklentisinin içinde varolan bir çalışma sayfası seçmek istiyorsanız veya çalışma sayfası belge düzeyi özelleştirmesinde çalışma zamanında oluşturulduysa, <xref:Microsoft.Office.Interop.Excel.Sheets> Excel çalışma kitabının Excel koleksiyonunu kullanarak erişmeniz gerekir; Aksi takdirde, <xref:Microsoft.Office.Tools.Excel.Worksheet> ana bilgisayar öğesine doğrudan erişebilirsiniz.

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
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
