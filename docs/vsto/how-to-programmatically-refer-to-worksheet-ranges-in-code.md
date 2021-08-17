---
title: 'Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek'
description: Visual Studio çalışma sayfasındaki NamedRange denetimi veya yerel Excel aralığı nesnesinin içeriğine program aracılığıyla başvurmak için Microsoft Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: be0052005ecc7af763aa1f4f934ef529afa4d4c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032777"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek
  Bir denetimin içeriğine veya yerel bir Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> nesnesine başvurmak için benzer bir işlem kullanırsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Aşağıdaki örnek çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.NamedRange> bir ekler ve ardından aralıkta hücreye metin ekler.

### <a name="to-refer-to-a-namedrange-control"></a>NamedRange denetimine başvurmak için

1. Denetimin özelliğine <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> bir dize <xref:Microsoft.Office.Tools.Excel.NamedRange> attayabilirsiniz. Bu kod, sınıfında değil, bir sayfa sınıfına `ThisWorkbook` yerleştirilsin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Yerel veri Excel kullanma
 Aşağıdaki örnek çalışma sayfasına yerel Excel aralığı ekler ve ardından aralıkta hücreye metin ekler.

### <a name="to-refer-to-a-native-range-object"></a>Yerel aralık nesnesine başvurmak için

1. Aralığın özelliğine <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> bir dize attayabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [Nasıllı: Çalışma sayfasında program aracılığıyla yazım denetimi yapma](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: Aralıkları artımlı olarak değişen verilerle program aracılığıyla otomatik olarak doldurma](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Nasıl olur: Çalışma sayfası aralıklarında program aracılığıyla metin arama](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
