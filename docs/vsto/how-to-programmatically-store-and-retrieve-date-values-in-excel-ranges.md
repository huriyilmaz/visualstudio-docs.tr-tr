---
title: tarih değerlerini program aracılığıyla Excel aralıklarında depola & al
description: Microsoft Excel aralıklarında tarih değerlerini programlı bir şekilde depolamak ve almak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c9dbf0d63b13d6f7b66fc24c82a80e7fecea5d4c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025971"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>nasıl yapılır: program aracılığıyla Excel aralıklarında tarih değerlerini depolama ve alma
  değerleri bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim veya yerel Excel aralığı nesnesinde depolayıp alabilir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Visual Studio Office geliştirme araçlarını kullanarak bir aralıktaki 1/1/1900 veya sonraki bir tarih değerini depolarsanız OLE Automation (OA) biçiminde depolanır. <xref:System.DateTime.FromOADate%2A>OLE Otomasyonu (OA) tarihlerinin değerini almak için yöntemini kullanmanız gerekir. Tarih 1/1/1900 ' den daha eski ise, bir dize olarak depolanır.

> [!NOTE]
> Excel tarihler, 1900 ilk iki aya ait OLE otomasyon tarihlerinden farklıdır. Ayrıca, **1904 tarih sistemi** seçeneği işaretliyse farklılık da vardır. Aşağıdaki kod örnekleri bu farklılıkları gidermez.

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma

- Bu örnek, belge düzeyi özelleştirmeleri içindir. Aşağıdaki kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

### <a name="to-store-a-date-value-in-a-named-range"></a>Adlandırılmış bir aralıkta bir tarih değeri depolamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresinde bir denetim oluştur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Bugünün tarihini değerini olarak ayarlayın `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Adlandırılmış bir aralıktan tarih değeri almak için

1. Tarih değerini öğesinden alın `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>yerel Excel aralıklarını kullan

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>yerel Excel aralığı nesnesinde bir tarih değeri depolamak için

1. <xref:Microsoft.Office.Interop.Excel.Range> **A1** hücresini temsil eden bir oluştur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Bugünün tarihini değerini olarak ayarlayın `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>yerel Excel range nesnesinden bir tarih değeri almak için

1. Tarih değerini öğesinden alın `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
