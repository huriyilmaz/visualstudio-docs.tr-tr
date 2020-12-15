---
title: 'Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma'
description: Visual Studio 'Yu kullanarak bir Microsoft Excel çalışma kitabında hesaplamaları programlı bir şekilde nasıl çalıştırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9f385e7c58972844c30320c680f42d8394580d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524693"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde veya yerel Excel Aralık nesnesinde hesaplamalar çalıştırmak için benzer bir işlem kullanırsınız.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>NamedRange Denetiminde hesaplamalar çalıştırma
 Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> a1 hücresini oluşturur ve sonra hücreyi hesaplar. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Bir NamedRange Denetiminde hesaplamalar çalıştırmak için

1. Adlandırılmış aralığı oluşturun.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A>Belirtilen aralığın yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Yerel bir Excel aralığında hesaplamalar çalıştırma

### <a name="to-run-calculations-in-a-native-excel-range"></a>Yerel bir Excel aralığında hesaplamalar çalıştırmak için

1. Adlandırılmış aralığı oluşturun.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A>Belirtilen aralığın yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
