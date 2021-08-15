---
title: 'nasıl yapılır: program aracılığıyla Excel hesaplamaları çalıştırma'
description: bir Microsoft Excel çalışma kitabındaki hesaplamaları programlı olarak çalıştırmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 234457e235a78281858a45a202fdeff9ff781a849fef5a5757ad505f368cd023
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384242"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>nasıl yapılır: program aracılığıyla Excel hesaplamaları çalıştırma
  bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde veya yerel Excel aralığı nesnesinde hesaplamalar çalıştırmak için benzer bir işlem kullanırsınız.

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

## <a name="run-calculations-in-a-native-excel-range"></a>yerel Excel aralığında hesaplamalar çalıştırma

### <a name="to-run-calculations-in-a-native-excel-range"></a>yerel bir Excel aralığında hesaplamalar çalıştırmak için

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
