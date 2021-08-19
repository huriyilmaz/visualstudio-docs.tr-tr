---
title: 'Nasıl yapılır: çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listeleme'
description: Visual Studio kullanarak Microsoft Excel çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla nasıl listeleyeceğinizi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b62b2bdb5fdff99a42cb0967e005b6c907ffbe76
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122676"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Nasıl yapılır: çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listeleme
  <xref:Microsoft.Office.Interop.Excel.Workbook>Sınıfı bir nesne sağlar <xref:Microsoft.Office.Interop.Excel.Worksheets> . Bu nesne çalışma kitabındaki tüm nesnelerin bir koleksiyonunu içerir <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki çalışma kitabındaki tüm mevcut çalışma sayfalarını listelemek için

1. Koleksiyonda yineleme yapın <xref:Microsoft.Office.Interop.Excel.Worksheets> ve her sayfanın adını bir denetimden bir hücre uzaklığa gönderin <xref:Microsoft.Office.Tools.Excel.NamedRange> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>VSTO eklenti içindeki çalışma kitabındaki tüm mevcut çalışma sayfalarını listelemek için

1. Koleksiyonda yineleme yapın <xref:Microsoft.Office.Interop.Excel.Worksheets> ve her sayfanın adını bir nesneden bir hücre uzaklığa gönderin <xref:Microsoft.Office.Interop.Excel.Range> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
