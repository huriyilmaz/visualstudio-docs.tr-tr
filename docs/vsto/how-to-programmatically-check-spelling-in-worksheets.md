---
title: 'Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme'
description: Microsoft Excel çalışma sayfasında program aracılığıyla kelimelerin yazımını nasıl denetleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826063"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme
  Çalışma sayfasında program aracılığıyla kelimelerin yazımını denetleyebilirsiniz. Çalışma sayfasında yanlış yazılmış kelimeler varsa, **Yazım denetimi** iletişim kutusu otomatik olarak görüntülenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A>Etkin çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
