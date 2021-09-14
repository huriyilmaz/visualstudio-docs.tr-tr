---
title: 'Nasıl yapılır: çalışma sayfalarındaki verileri program aracılığıyla sıralama'
description: çalışma zamanında çalışma sayfası aralıklarına ve listelerinde bulunan verileri programlı bir şekilde sıralamak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 70d99cb76530f6f5b0452063c2d1d0aa21629e34
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633878"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Nasıl yapılır: çalışma sayfalarındaki verileri program aracılığıyla sıralama
  Çalışma zamanında çalışma sayfası aralıkları ve listelerinde bulunan verileri sıralayabilirsiniz. Aşağıdaki kod, ilk sütundaki verilerin adlı çok sütunlu bir aralığı `Fruits` ve sonra ikinci sütundaki verileri sıralar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki verileri sıralama

### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange denetimindeki verileri sıralamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A>Denetimin yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.NamedRange> . Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasında adlı bir denetim gerektirir `Fruits` . Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Bir denetimdeki verileri sıralamak için *Sheet1. vb* veya *Sayfa1. cs* ' ye aşağıdaki kodu koyun <xref:Microsoft.Office.Tools.Excel.ListObject> . Kod, <xref:Microsoft.Office.Tools.Excel.ListObject> `fruitList` adlı bir çalışma sayfasında adlı bir denetime sahip olduğunuzu varsayar `Sheet1` .

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetimindeki verileri sıralamak için

1. <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> Konak denetiminin özelliğinin yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.ListObject> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>VSTO eklenti içindeki verileri sıralama

### <a name="to-sort-data-in-a-native-range"></a>Yerel aralıktaki verileri sıralamak için

1. <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>yerel Excel denetiminin yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.Range> . aşağıdaki örnek, bir çalışma sayfasında adlı yerel bir Excel denetimi gerektirir `Fruits` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>ListObject denetimindeki verileri sıralamak için

1. <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> yerel Excel denetiminin özelliğinin yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.ListObject> . aşağıdaki örnek, <xref:Microsoft.Office.Interop.Excel.ListObject> etkin çalışma sayfasında adlı yerel bir Excel denetimine sahip olduğunuzu varsayar `fruitList` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: artımlı değişen verilerle aralıkları program aracılığıyla otomatik olarak doldur](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
