---
title: 'Nasıllı: Çalışma sayfasında program aracılığıyla yazım denetimi yapma'
description: Çalışma sayfasındaki sözcüklerin yazımını program aracılığıyla denetlemeyi Microsoft Excel öğrenin.
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
ms.openlocfilehash: a91c038b53e7d28c962c7fe8cede1d2f63e99bbbdd0d2984ff8e029b1644adf7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394482"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Nasıllı: Çalışma sayfasında program aracılığıyla yazım denetimi yapma
  Program aracılığıyla bir çalışma sayfasındaki sözcüklerin yazımını kontrol edin. Çalışma **sayfasında** yanlış yazılmış sözcükler varsa, Yazım Denetimi iletişim kutusu otomatik olarak görüntülenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmede çalışma sayfasında yazım denetimi yapmak için

1. Çalışma <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> sayfasının yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Çalışma sayfasındaki bir eklentide yazım denetimi VSTO için

1. Etkin <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> çalışma sayfasının yöntemini çağırma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: Program aracılığıyla Excel çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
