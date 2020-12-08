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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f2a9f50767082ead9daafe684aae7fc1524ba9c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848297"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme
  Çalışma sayfasında program aracılığıyla kelimelerin yazımını denetleyebilirsiniz. Çalışma sayfasında yanlış yazılmış kelimeler varsa, **Yazım denetimi** iletişim kutusu otomatik olarak görüntülenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Çalışma sayfasının yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma sayfasında yazım denetimi yapmak için

1. <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A>Etkin çalışma sayfasının yöntemini çağırın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
