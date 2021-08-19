---
title: 'Nasıl yapılanlar: Çalışma kitaplarında çalışma sayfalarını program aracılığıyla taşıma'
description: Bir çalışma kitabındaki diğer çalışma sayfalarına göre çalışma sayfalarının konumunu program aracılığıyla Microsoft Excel öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: aeef102362d5471aa3be34e154cd73d8341ff834
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155895"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Nasıl yapılanlar: Çalışma kitaplarında çalışma sayfalarını program aracılığıyla taşıma
  Program aracılığıyla çalışma sayfalarının konumunu çalışma kitabındaki diğer çalışma sayfalarına göre değiştirebilirsiniz. Taşınan sayfa için bir konum belirtmezseniz, Excel yeni bir çalışma kitabı oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Belge düzeyi özelleştirmede çalışma sayfasını taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son sayfa olacak şekilde hareket ettirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Çalışma sayfasını bir çalışma VSTO taşımak için

1. Çalışma kitabındaki toplam sayfa sayısını bir değişkene atayın ve ardından ilk çalışma sayfasını son sayfa olacak şekilde hareket ettirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarından program aracılığıyla çalışma sayfalarını silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Nasıl yapılanlar: Çalışma sayfalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-worksheets.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
