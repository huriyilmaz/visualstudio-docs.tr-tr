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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823970"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde veya yerel Excel Aralık nesnesinde hesaplamalar çalıştırmak için benzer bir işlem kullanırsınız.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>NamedRange Denetiminde hesaplamalar çalıştırma
 Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> a1 hücresini oluşturur ve sonra hücreyi hesaplar. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Bir NamedRange Denetiminde hesaplamalar çalıştırmak için

1. Adlandırılmış aralığı oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A>Belirtilen aralığın yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Yerel bir Excel aralığında hesaplamalar çalıştırma

### <a name="to-run-calculations-in-a-native-excel-range"></a>Yerel bir Excel aralığında hesaplamalar çalıştırmak için

1. Adlandırılmış aralığı oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A>Belirtilen aralığın yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
