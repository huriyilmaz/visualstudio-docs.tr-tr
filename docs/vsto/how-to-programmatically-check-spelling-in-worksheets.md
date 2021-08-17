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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d45cafb20c1d021a893b5b650dff938f9ff5927e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026219"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme
  Çalışma sayfasında program aracılığıyla kelimelerin yazımını denetleyebilirsiniz. Çalışma sayfasında yanlış yazılmış kelimeler varsa, **Yazım denetimi** iletişim kutusu otomatik olarak görüntülenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>VSTO eklentisinin çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A>Etkin çalışma sayfasının yöntemini çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [nasıl yapılır: program aracılığıyla Excel hesaplamaları çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
