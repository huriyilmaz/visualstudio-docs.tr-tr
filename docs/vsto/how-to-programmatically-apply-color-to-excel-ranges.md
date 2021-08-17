---
title: 'Nasıl yapılır: Excel aralıklara program aracılığıyla renk uygulama'
description: Bir hücre aralığı içindeki metne renk uygulamak için NamedRange denetimi veya yerel bir Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3de687879a74c92c39331ca6668e29d7a3c77014a19cd3c7138eb396f2b52c78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384359"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Nasıl yapılır: Excel aralıklara program aracılığıyla renk uygulama
  Bir hücre aralığı içindeki metne renk uygulamak için bir denetim veya yerel bir Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> nesnesi kullanın.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>NamedRange denetimi kullanma
 Bu örnek, belge düzeyinde özelleştirmelere örnektir.

### <a name="to-apply-color-to-a-namedrange-control"></a>NamedRange denetimine renk uygulamak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>A1 hücresinde bir denetim oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Denetimde metnin rengini <xref:Microsoft.Office.Tools.Excel.NamedRange> ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Yerel veri Excel kullanma

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Yerel bir Excel aralığı nesnesine renk uygulamak için

1. A1 hücresinde bir aralık oluşturun ve metnin rengini ayarlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Ayrıca bkz.
- [Aralıklarla çalışma](../vsto/working-with-ranges.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Nasıl yapılanlar: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
