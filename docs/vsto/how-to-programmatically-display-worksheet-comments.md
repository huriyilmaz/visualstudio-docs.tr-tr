---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme'
description: Belge düzeyinde veya uygulama düzeyinde Microsoft Excel çalışma sayfasındaki açıklamaları program aracılığıyla nasıl gösterip gizleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 33ae98f6b6e4508f76323b0b06dab3693f0ac5d0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525843"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme
  Microsoft Office Excel çalışma sayfalarındaki açıklamaları programlı bir şekilde gösterebilir ve gizleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasındaki tüm açıklamaları göstermek için

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Uygulama düzeyindeki bir VSTO eklentisinin çalışma sayfasındaki tüm açıklamaları görüntüleme

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
