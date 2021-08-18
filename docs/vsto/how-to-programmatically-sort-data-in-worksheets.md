---
title: 'Nasıl kullanılır: Çalışma sayfalarına program aracılığıyla veri sıralama'
description: Çalışma zamanında çalışma Visual Studio ve listelerde bulunan verileri program aracılığıyla sıralamak için bu verileri nasıl kullanabileceğiniz hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 073ad50f3bc5bc135e6fd7f22afcbaac721f8d99e08c8862816672387c111b32
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440688"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Nasıl kullanılır: Çalışma sayfalarına program aracılığıyla veri sıralama
  Çalışma zamanında çalışma sayfası aralıklarında ve listelerinde yer alan verileri sıraleyebilirsiniz. Aşağıdaki kod, ilk sütundaki verilere göre ve ardından ikinci sütundaki verilere `Fruits` göre adlı çok sütunlu bir aralığı sıralar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede verileri sıralama

### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange denetiminde verileri sıralamak için

1. Denetimin <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> yöntemini <xref:Microsoft.Office.Tools.Excel.NamedRange> çağırma. Aşağıdaki örnek, çalışma sayfasında <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı `Fruits` bir denetim gerektirir. Bu kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Denetimde verileri sıralamak *için aşağıdaki kodu Sheet1.vb* *veya Sheet1.cs'ye* <xref:Microsoft.Office.Tools.Excel.ListObject> girin. Kod, adlı çalışma sayfasında adlı <xref:Microsoft.Office.Tools.Excel.ListObject> bir `fruitList` denetime sahip olduğunu `Sheet1` varsayıyor.

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetiminde verileri sıralamak için

1. Konak <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> denetimi <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> özelliğinin <xref:Microsoft.Office.Tools.Excel.ListObject> yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Bir eklentide VSTO sıralama

### <a name="to-sort-data-in-a-native-range"></a>Verileri yerel bir aralıkta sıralamak için

1. Yerel <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> denetim denetimi Excel <xref:Microsoft.Office.Interop.Excel.Range> çağırma. Aşağıdaki örnek, çalışma sayfasında adlı Excel yerel bir `Fruits` denetim gerektirir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetiminde verileri sıralamak için

1. Yerel <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> denetim denetimi <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> özelliğinin yöntemini <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. Aşağıdaki örnekte, etkin çalışma sayfasında adlı Excel <xref:Microsoft.Office.Interop.Excel.ListObject> yerel bir çalışma alanı `fruitList` denetimine sahip olduğunu varsayabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: Aralıkları artımlı olarak değişen verilerle program aracılığıyla otomatik olarak doldurma](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
