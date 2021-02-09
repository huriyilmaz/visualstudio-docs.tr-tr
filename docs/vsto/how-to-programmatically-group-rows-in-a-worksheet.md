---
title: 'Nasıl yapılır: çalışma sayfasında program aracılığıyla satırları gruplama'
description: Bir NamedRange denetimi veya yerel Excel Range nesnesi kullanarak Microsoft Excel 'de bir veya daha fazla satırı programlı bir şekilde nasıl gruplandıralabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaa0bbcc2c26a36e43e862cbe5a8f117c2a1fb26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885423"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Nasıl yapılır: çalışma sayfasında program aracılığıyla satırları gruplama
  Bir veya daha çok tam satırı gruplandırabilirsiniz. Çalışma sayfasında bir grup oluşturmak için, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim veya yerel Excel Aralık nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Tasarım zamanında belge düzeyi projesine bir denetim eklerseniz, bu denetimi program aracılığıyla bir grup oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> aynı çalışma sayfasında üç denetimin olduğunu varsayar: `data2001` , `data2002` ve `dataAll` . Her bir adlandırılmış aralık çalışma sayfasındaki tüm bir satırı ifade eder.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Çalışma sayfasında NamedRange denetimleri grubu oluşturmak için

1. Her bir aralığın yöntemini çağırarak üç adlandırılmış aralığı gruplayın <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> . Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Satırları çözmek için <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> yöntemini çağırın.

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan
 Kod,, `data2001` `data2002` , ve bir çalışma sayfasında adlı üç Excel aralığınız olduğunu varsayar `dataAll` .

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Çalışma sayfasında Excel aralıkları grubu oluşturmak için

1. Her bir aralığın yöntemini çağırarak üç adlandırılmış aralığı gruplayın <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> . Aşağıdaki örnek,, <xref:Microsoft.Office.Interop.Excel.Range> ve adlı üç denetimin `data2001` `data2002` `dataAll` aynı çalışma sayfasında olduğunu varsayar. Her bir adlandırılmış aralık çalışma sayfasındaki tüm bir satırı ifade eder.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Satırları çözmek için <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
