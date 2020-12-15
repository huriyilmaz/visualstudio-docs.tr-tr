---
title: Excel aralıklarında program aracılığıyla tarih değerlerini depolama & alma
description: Microsoft Excel aralıklarında tarih değerlerini programlı bir şekilde depolamak ve almak için Visual Studio 'Yu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 673969e13b2f49b91416d730533be0f075813781
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523581"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Nasıl yapılır: program aracılığıyla Excel aralıklarında tarih değerlerini depolama ve alma
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde veya yerel Excel Aralık nesnesinde değerleri saklayabilir ve alabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Visual Studio 'da Office geliştirme araçları 'nı kullanarak bir aralıktaki 1/1/1900 veya sonraki bir tarih değerini depolarsanız, OLE Automation (OA) biçiminde depolanır. <xref:System.DateTime.FromOADate%2A>OLE Otomasyonu (OA) tarihlerinin değerini almak için yöntemini kullanmanız gerekir. Tarih 1/1/1900 ' den daha eski ise, bir dize olarak depolanır.

> [!NOTE]
> Excel tarihleri, 1900 ayın ilk iki ayı için OLE Otomasyon tarihlerinden farklıdır. Ayrıca, **1904 tarih sistemi** seçeneği işaretliyse farklılık da vardır. Aşağıdaki kod örnekleri bu farklılıkları gidermez.

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma

- Bu örnek, belge düzeyi özelleştirmeleri içindir. Aşağıdaki kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

### <a name="to-store-a-date-value-in-a-named-range"></a>Adlandırılmış bir aralıkta bir tarih değeri depolamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresinde bir denetim oluştur.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Bugünün tarihini değerini olarak ayarlayın `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Adlandırılmış bir aralıktan tarih değeri almak için

1. Tarih değerini öğesinden alın `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Yerel Excel Aralık nesnesinde bir tarih değeri depolamak için

1. <xref:Microsoft.Office.Interop.Excel.Range> **A1** hücresini temsil eden bir oluştur.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Bugünün tarihini değerini olarak ayarlayın `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Yerel Excel Aralık nesnesinden bir tarih değeri almak için

1. Tarih değerini öğesinden alın `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
