---
title: 'Nasıl yapılır: çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listeleme'
description: Visual Studio 'Yu kullanarak bir Microsoft Excel çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla nasıl listeleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74ff02d6458e643e9a143a8132ad16f10899ec74
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525658"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Nasıl yapılır: çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listeleme
  <xref:Microsoft.Office.Interop.Excel.Workbook>Sınıfı bir nesne sağlar <xref:Microsoft.Office.Interop.Excel.Worksheets> . Bu nesne çalışma kitabındaki tüm nesnelerin bir koleksiyonunu içerir <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma kitabındaki tüm mevcut çalışma sayfalarını listelemek için

1. Koleksiyonda yineleme yapın <xref:Microsoft.Office.Interop.Excel.Worksheets> ve her sayfanın adını bir denetimden bir hücre uzaklığa gönderin <xref:Microsoft.Office.Tools.Excel.NamedRange> .

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Bir VSTO eklentisinin çalışma kitabındaki tüm mevcut çalışma sayfalarını listelemek için

1. Koleksiyonda yineleme yapın <xref:Microsoft.Office.Interop.Excel.Worksheets> ve her sayfanın adını bir nesneden bir hücre uzaklığa gönderin <xref:Microsoft.Office.Interop.Excel.Range> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
