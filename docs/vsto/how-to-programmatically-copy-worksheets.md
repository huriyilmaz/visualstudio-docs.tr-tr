---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfalarını kopyalama'
description: Çalışma kitabının bir kopyasını nasıl oluşturabileceğinizi ve bu çalışma kitabını çalışma kitabındaki mevcut bir çalışma sayfasından önce veya sonra eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a5b24d7896ec1f81c7e8d5d4c41a5e6af807b13
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828585"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Nasıl yapılır: program aracılığıyla çalışma sayfalarını kopyalama
  Çalışma kitabının bir kopyasını oluşturabilir ve bu çalışma sayfasını çalışma kitabındaki mevcut çalışma sayfasından önce veya sonra ekleyebilirsiniz. Çalışma sayfasının ekleneceği yeri belirtmezseniz, Excel yeni çalışma sayfasını içeren yeni bir çalışma kitabı oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Çalışma sayfasını programlı bir şekilde kopyalamayın veya son kullanıcı çalışma sayfasını el ile kopyalamadığında yeni çalışma sayfasının arkasında hiçbir kod yoktur ve yeni çalışma sayfasındaki denetimler çalışmaz. Bunun nedeni, yeni kopyalanmış çalışma sayfasının bir <xref:Microsoft.Office.Interop.Excel.Worksheet> konak öğesi değil bir nesne olmasından kaynaklanır <xref:Microsoft.Office.Tools.Excel.Worksheet> . Windows Forms denetimleri ve konak denetimleri, yalnızca konak öğelerine eklenebilir. Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma kitabına kopyalanmış çalışma sayfası eklemek için

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>Geçerli çalışma kitabındaki ilk çalışma sayfasını kopyalamak ve kopyayı üçüncü sayfadan sonra yerleştirmek için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma kitabına kopyalanmış çalışma sayfası eklemek için

1. <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>Geçerli çalışma kitabındaki ilk çalışma sayfasını kopyalamak ve kopyayı üçüncü sayfadan sonra yerleştirmek için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme](../vsto/how-to-programmatically-select-worksheets.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
