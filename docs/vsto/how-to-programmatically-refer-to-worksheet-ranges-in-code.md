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
ms.openlocfilehash: 89a4b7c594f942405777145f94ed0a3503e9b16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963763"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimin veya yerel Excel Aralık nesnesinin içeriğine başvurmak için benzer bir işlem kullanırsınız.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Aşağıdaki örnek bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasına bir ekler ve sonra aralıktaki hücreye metin ekler.

### <a name="to-refer-to-a-namedrange-control"></a>NamedRange denetimine başvurmak için

1. Denetimin özelliğine bir dize atayın <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> . Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan
 Aşağıdaki örnek, bir çalışma sayfasına yerel bir Excel aralığı ekler ve sonra aralıktaki hücreye metin ekler.

### <a name="to-refer-to-a-native-range-object"></a>Yerel bir Aralık nesnesine başvurmak için

1. Aralığın özelliğine bir dize atayın <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> .

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

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
