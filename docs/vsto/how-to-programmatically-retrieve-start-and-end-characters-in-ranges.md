---
title: Aralıklarda program aracılığıyla başlangıç & bitiş karakterlerini al
description: Bu örnek, bir aralığın başlangıç ve bitiş konumlarının karakter konumlarını nasıl alabileceğinizi gösterir.
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 76b5c367223731518a9f09899259d7d7534a76a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105892"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma
  Bu örnek, bir aralığın başlangıç ve bitiş konumlarının karakter konumlarını nasıl alabileceğinizi gösterir.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığın başlangıç ve bitiş karakterlerini almak için

1. <xref:Microsoft.Office.Interop.Word.Range.Start%2A>Nesnesinin ve özelliklerinin değerlerini alın <xref:Microsoft.Office.Interop.Word.Range.End%2A> <xref:Microsoft.Office.Interop.Word.Range> . Aşağıdaki kod örneği belgedeki ikinci tümcenin başlangıç ve bitiş konumunu alır. Bu kod örneğini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet25":::

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>VSTO eklentisi kullanarak bir aralığın başlangıç ve bitiş karakterlerini almak için

1. <xref:Microsoft.Office.Interop.Word.Range.Start%2A>Nesnesinin ve özelliklerinin değerlerini alın <xref:Microsoft.Office.Interop.Word.Range.End%2A> <xref:Microsoft.Office.Interop.Word.Range> . Aşağıdaki kod örneği, etkin belgedeki ikinci tümcenin başlangıç ve bitiş konumunu alır. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet25":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Nasıl yapılır: belgelerde program aracılığıyla karakter sayma](../vsto/how-to-programmatically-count-characters-in-documents.md)
