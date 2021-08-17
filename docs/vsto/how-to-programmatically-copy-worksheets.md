---
title: 'Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla kopyalama'
description: Çalışma sayfasının bir kopyasını oluşturma ve bu çalışma sayfasını çalışma kitabındaki mevcut çalışma sayfasından önce veya sonra ekleme hakkında bilgi alın.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7aed53b3579e656d3b00e200b38075859174b8cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106217"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla kopyalama
  Çalışma sayfasının bir kopyasını oluşturabilir ve bu çalışma sayfasını çalışma kitabındaki mevcut çalışma sayfasından önce veya sonra ekleyebilirsiniz. Çalışma sayfasını nereye ekleymezseniz, çalışma Excel yeni çalışma sayfasını içermesi için yeni bir çalışma kitabı oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Çalışma sayfasını program aracılığıyla kopyalamanız veya son kullanıcının çalışma sayfasını el ile kopyalaması, yeni çalışma sayfasının ardında kod yoktur ve yeni çalışma sayfasındaki denetimler çalışmaz. Bunun nedeni, yeni kopyalanan çalışma sayfasının bir konak <xref:Microsoft.Office.Interop.Excel.Worksheet> öğesi değil bir <xref:Microsoft.Office.Tools.Excel.Worksheet> nesnedir. Windows Form denetimleri ve konak denetimleri yalnızca konak öğelerine eklenebilir. Daha fazla bilgi için [bkz. Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede bir çalışma kitabına kopyalanmış çalışma sayfası eklemek için

1. Geçerli çalışma <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> kitabındaki ilk çalışma sayfasını kopyalamak ve kopyayı üçüncü sayfadan sonra eklemek için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Bir çalışma kitabına kopyalanmış çalışma sayfası eklemek için VSTO ekleme

1. Geçerli çalışma <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> kitabındaki ilk çalışma sayfasını kopyalamak ve kopyayı üçüncü sayfadan sonra eklemek için yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılanlar: Çalışma kitaplarında program aracılığıyla yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılanlar: Çalışma kitaplarından program aracılığıyla çalışma sayfalarını silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma sayfalarını seçme](../vsto/how-to-programmatically-select-worksheets.md)
- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
