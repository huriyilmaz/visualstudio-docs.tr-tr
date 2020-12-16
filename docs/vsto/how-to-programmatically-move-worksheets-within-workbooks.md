---
title: 'Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma'
description: Microsoft Excel çalışma kitabındaki diğer çalışma sayfalarına göre çalışma sayfalarının konumunu programlı bir şekilde nasıl değiştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 165ac8f440b33d68dc70530731a5528ae23726b0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525588"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma
  Çalışma sayfalarındaki diğer çalışma sayfalarına göre çalışma sayfalarının konumunu programlı bir şekilde değiştirebilirsiniz. Taşınan sayfa için bir konum belirtmezseniz, Excel bu dosyayı içeren yeni bir çalışma kitabı oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasını taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son bir duruma gelecek şekilde taşıyın.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>VSTO eklentideki bir çalışma sayfasını taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son bir duruma gelecek şekilde taşıyın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
