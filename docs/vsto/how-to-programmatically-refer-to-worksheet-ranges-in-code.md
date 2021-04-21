---
title: 'Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma'
description: Visual Studio 'Yu, bir Microsoft Excel çalışma sayfasındaki NamedRange denetimi veya yerel Excel Range nesnesinin içeriğine programlı bir şekilde başvurmak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ea4e3da3c67d55aedea0d85a0a35b8ed2cf93b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827090"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimin veya yerel Excel Aralık nesnesinin içeriğine başvurmak için benzer bir işlem kullanırsınız.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Aşağıdaki örnek bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasına bir ekler ve sonra aralıktaki hücreye metin ekler.

### <a name="to-refer-to-a-namedrange-control"></a>NamedRange denetimine başvurmak için

1. Denetimin özelliğine bir dize atayın <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> . Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan
 Aşağıdaki örnek, bir çalışma sayfasına yerel bir Excel aralığı ekler ve sonra aralıktaki hücreye metin ekler.

### <a name="to-refer-to-a-native-range-object"></a>Yerel bir Aralık nesnesine başvurmak için

1. Aralığın özelliğine bir dize atayın <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: artımlı değişen verilerle aralıkları program aracılığıyla otomatik olarak doldur](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
