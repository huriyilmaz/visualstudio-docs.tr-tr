---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme'
description: belge düzeyinde veya uygulama düzeyinde Microsoft Excel çalışma sayfasında açıklamaları program aracılığıyla nasıl gösterip gizleyebileceğinizi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 614fea5dc82ebd79096a81ea96d26a0a84216678
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083251"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme
  Microsoft Office Excel çalışma sayfalarında program aracılığıyla açıklamaları görüntüleyebilir ve gizleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasındaki tüm açıklamaları göstermek için

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**. Bu kod, sınıfında değil, bir sayfa sınıfına yerleştirilmelidir `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>uygulama düzeyindeki VSTO eklenti içindeki çalışma sayfasındaki tüm açıklamaları görüntüleme

1. <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>Açıklamaları göstermek istiyorsanız özelliği **true** olarak ayarlayın; Aksi takdirde **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
