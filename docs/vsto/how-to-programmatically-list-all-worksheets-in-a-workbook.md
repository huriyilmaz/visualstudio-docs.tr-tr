---
title: 'Nasıl olur: Çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listele'
description: Bir çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla, Microsoft Excel kullanarak nasıl listeleyebilirsiniz Visual Studio.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633921"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Nasıl olur: Çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listele
  sınıfı <xref:Microsoft.Office.Interop.Excel.Workbook> bir nesnesi <xref:Microsoft.Office.Interop.Excel.Worksheets> sağlar. Bu nesne, çalışma kitabındaki tüm <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnelerin bir koleksiyonunu içerir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Bir çalışma kitabındaki tüm mevcut çalışma sayfalarını belge düzeyinde özelleştirmede listele

1. Koleksiyonda devam <xref:Microsoft.Office.Interop.Excel.Worksheets> etmek ve her bir sayfa adını bir denetimden hücre uzaklığına <xref:Microsoft.Office.Tools.Excel.NamedRange> göndermek.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Bir çalışma kitabındaki tüm mevcut çalışma sayfalarını bir çalışma kitabı VSTO için

1. Koleksiyonda devam <xref:Microsoft.Office.Interop.Excel.Worksheets> eder ve her bir sayfa adını bir nesneden bir hücre uzaklığına <xref:Microsoft.Office.Interop.Excel.Range> gönderir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılanlar: Çalışma kitaplarında program aracılığıyla yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Nasıl yapılanlar: Çalışma kitaplarında çalışma sayfalarını program aracılığıyla taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Office projelerinde nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
