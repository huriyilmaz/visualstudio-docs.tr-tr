---
title: 'Nasıl yapılır: program aracılığıyla Excel aralıklarına renk uygulama'
description: Bir hücre aralığı içindeki metne renk uygulamayı öğrenin, NamedRange denetimi veya yerel Excel Range nesnesi kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7ab1681cf402fc45b81b49b77a84973be83729c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910099"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Nasıl yapılır: program aracılığıyla Excel aralıklarına renk uygulama
  Bir hücre aralığı içindeki metne renk uygulamak için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim veya yerel Excel Aralık nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Bu örnek, belge düzeyi özelleştirmeleri içindir.

### <a name="to-apply-color-to-a-namedrange-control"></a>NamedRange denetimine renk uygulamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 hücresinde bir denetim oluştur.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Denetimdeki metnin rengini ayarlayın <xref:Microsoft.Office.Tools.Excel.NamedRange> .

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Yerel Excel Aralık nesnesine renk uygulamak için

1. A1 hücresinde bir Aralık oluşturun ve sonra metnin rengini ayarlayın.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
