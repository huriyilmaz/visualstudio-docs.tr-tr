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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827298"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma
  Çalışma sayfalarındaki diğer çalışma sayfalarına göre çalışma sayfalarının konumunu programlı bir şekilde değiştirebilirsiniz. Taşınan sayfa için bir konum belirtmezseniz, Excel bu dosyayı içeren yeni bir çalışma kitabı oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma sayfasını taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son bir duruma gelecek şekilde taşıyın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>VSTO eklentideki bir çalışma sayfasını taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son bir duruma gelecek şekilde taşıyın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
