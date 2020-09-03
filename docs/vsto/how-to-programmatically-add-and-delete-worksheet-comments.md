---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc02a659c50a5b207f2f53d0a8781b0d23419301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520087"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme
  Microsoft Office Excel çalışma sayfalarında program aracılığıyla açıklama ekleyip silebilirsiniz. Açıklamalar yalnızca tek hücrelere eklenebilir, çok hücreli aralıklar için kullanılamaz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Belge düzeyi projede açıklama ekleme ve silme
 Aşağıdaki örneklerde <xref:Microsoft.Office.Tools.Excel.NamedRange> `dateComment` adlı bir çalışma sayfasında adlı tek hücreli bir denetimin olduğu varsayılır `Sheet1` .

### <a name="to-add-a-new-comment-to-a-named-range"></a>Adlandırılmış aralığa yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A>Denetimin yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.NamedRange> ve açıklama metnini sağlayın. Bu kodun sınıfa yerleştirilmesi gerekir `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>Adlandırılmış bir aralıktan yorumu silmek için

1. Aralıkta bir açıklamanın bulunduğunu doğrulayın ve silin. Bu kodun sınıfa yerleştirilmesi gerekir `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>VSTO eklenti projesinde yorum ekleme ve silme
 Aşağıdaki örneklerde, <xref:Microsoft.Office.Interop.Excel.Range> etkin çalışma sayfasında adlı tek bir hücre olduğu varsayılır `dateComment` .

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Excel aralığına yeni bir açıklama eklemek için

1. Yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> <xref:Microsoft.Office.Interop.Excel.Range> ve açıklama metnini sağlayın.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>Bir Excel aralığından bir yorumu silmek için

1. Aralıkta bir açıklamanın bulunduğunu doğrulayın ve silin.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
