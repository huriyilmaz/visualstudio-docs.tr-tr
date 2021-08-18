---
title: 'Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme'
description: Microsoft Office Excel çalışma sayfalarında program aracılığıyla açıklamaları nasıl ekleyebileceğiniz ve silebileceğinizi öğrenin. Çoklu hücre aralıklarına değil, yalnızca tek hücrelere açıklama ekleyebilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 04259cdb6f21254dba6c7769347403fbb6410f26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148161"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme
  Microsoft Office Excel çalışma sayfalarında program aracılığıyla açıklama ekleyip silebilirsiniz. Açıklamalar yalnızca tek hücrelere eklenebilir, çok hücreli aralıklar için kullanılamaz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Belge düzeyi projede açıklama ekleme ve silme
 Aşağıdaki örneklerde <xref:Microsoft.Office.Tools.Excel.NamedRange> `dateComment` adlı bir çalışma sayfasında adlı tek hücreli bir denetimin olduğu varsayılır `Sheet1` .

### <a name="to-add-a-new-comment-to-a-named-range"></a>Adlandırılmış aralığa yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A>Denetimin yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.NamedRange> ve açıklama metnini sağlayın. Bu kodun sınıfa yerleştirilmesi gerekir `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Adlandırılmış bir aralıktan yorumu silmek için

1. Aralıkta bir açıklamanın bulunduğunu doğrulayın ve silin. Bu kodun sınıfa yerleştirilmesi gerekir `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>VSTO eklenti projesinde açıklama ekleme ve silme
 Aşağıdaki örneklerde, <xref:Microsoft.Office.Interop.Excel.Range> etkin çalışma sayfasında adlı tek bir hücre olduğu varsayılır `dateComment` .

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Excel aralığa yeni bir açıklama eklemek için

1. Yöntemini çağırın <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> <xref:Microsoft.Office.Interop.Excel.Range> ve açıklama metnini sağlayın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Excel aralığından bir yorumu silmek için

1. Aralıkta bir açıklamanın bulunduğunu doğrulayın ve silin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma sayfalarıyla çalışma](../vsto/working-with-worksheets.md)
- [Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
