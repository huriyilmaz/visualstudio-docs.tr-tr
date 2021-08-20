---
title: 'Nasıl yapılır: çalışma sayfasında program aracılığıyla satırları gruplama'
description: NamedRange denetimi veya yerel bir Excel range nesnesi kullanarak Microsoft Excel bir veya daha fazla satırı programlı olarak nasıl gruplandıralabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 89d71b501dc7c9c65e2cf1d0d167b34233c30383
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148005"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Nasıl yapılır: çalışma sayfasında program aracılığıyla satırları gruplama
  Bir veya daha çok tam satırı gruplandırabilirsiniz. çalışma sayfasında bir grup oluşturmak için, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim veya yerel Excel range nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Tasarım zamanında belge düzeyi projesine bir denetim eklerseniz, bu denetimi program aracılığıyla bir grup oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> aynı çalışma sayfasında üç denetimin olduğunu varsayar: `data2001` , `data2002` ve `dataAll` . Her bir adlandırılmış aralık çalışma sayfasındaki tüm bir satırı ifade eder.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Çalışma sayfasında NamedRange denetimleri grubu oluşturmak için

1. Her bir aralığın yöntemini çağırarak üç adlandırılmış aralığı gruplayın <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> . Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Satırları çözmek için <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> yöntemini çağırın.

## <a name="use-native-excel-ranges"></a>yerel Excel aralıklarını kullan
 kod, `data2001` `data2002` bir çalışma sayfasında, ve adında üç Excel aralığa sahip olduğunuzu varsayar `dataAll` .

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>çalışma sayfasında bir Excel aralığı grubu oluşturmak için

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
