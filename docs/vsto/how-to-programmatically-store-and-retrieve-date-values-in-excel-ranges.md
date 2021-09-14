---
title: Tarih & program aracılığıyla veri Excel aralıklarında depolama
description: Tarih değerlerini program aracılığıyla Visual Studio ve aralıklarda almak için Microsoft Excel öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633870"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Nasıl kullanılır: Tarih değerlerini program aracılığıyla veri aralıklarında Excel alma
  Değerleri bir denetimde veya yerel bir Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> nesnesinde depolar ve alabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Visual Studio'de Office geliştirme araçlarını kullanarak 1/1/1900'den sonra gelen bir tarih değerini bir aralıkta depolarsanız, bu değer OLE Otomasyonu (OA) biçiminde depolanır. OLE Otomasyonu <xref:System.DateTime.FromOADate%2A> (OA) tarihlerinin değerini almak için yöntemini kullanabilirsiniz. Tarih 1/1/1900'den eski ise dize olarak depolanır.

> [!NOTE]
> Excel OLE Otomasyonu tarihlerinden 1900'e kadar olan ilk iki aydan farklıdır. **1904** tarih sistemi seçeneği işaretli ise farklılıklar da vardır. Aşağıdaki kod örnekleri bu farkları ele alamaz.

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma

- Bu örnek, belge düzeyinde özelleştirmelere örnektir. Aşağıdaki kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

### <a name="to-store-a-date-value-in-a-named-range"></a>Bir tarih değerini adlandırılmış bir aralıkta depolamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 hücresinde **bir denetim oluşturun.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Bugünün tarihini değeri olarak `NamedRange1` ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Adlandırılmış bir aralıktan tarih değeri almak için

1. tarih değerini değerinden `NamedRange1` alın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Yerel veri Excel kullanma

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Bir tarih değerini yerel bir Excel nesnesinde depolamak için

1. <xref:Microsoft.Office.Interop.Excel.Range>A1 hücresine temsil **eden bir oluşturun.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Bugünün tarihini değeri olarak `rng` ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Yerel bir Excel range nesnesinden tarih değeri almak için

1. tarih değerini değerinden `rng` alın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
