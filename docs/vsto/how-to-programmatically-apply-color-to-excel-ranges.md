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
ms.openlocfilehash: 081985dbd4b235fe5dd8d3472d0ab574603abe1b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828325"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Nasıl yapılır: program aracılığıyla Excel aralıklarına renk uygulama
  Bir hücre aralığı içindeki metne renk uygulamak için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim veya yerel Excel Aralık nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Bu örnek, belge düzeyi özelleştirmeleri içindir.

### <a name="to-apply-color-to-a-namedrange-control"></a>NamedRange denetimine renk uygulamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 hücresinde bir denetim oluştur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Denetimdeki metnin rengini ayarlayın <xref:Microsoft.Office.Tools.Excel.NamedRange> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Yerel Excel aralıklarını kullan

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Yerel Excel Aralık nesnesine renk uygulamak için

1. A1 hücresinde bir Aralık oluşturun ve sonra metnin rengini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
