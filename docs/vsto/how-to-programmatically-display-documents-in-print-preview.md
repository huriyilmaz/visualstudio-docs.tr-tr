---
title: 'Nasıl yapılır: belgeleri baskı önizlemede program aracılığıyla görüntüleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 036f8a45d5605b55b9743a22d598a13780641c97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545918"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Nasıl yapılır: belgeleri baskı önizlemede program aracılığıyla görüntüleme
  Çözümünüz bir rapor oluşturursa, raporu kullanıcıya baskı önizleme modunda görüntülemek isteyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri için yordamlar

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>PrintPreview yöntemini çağırarak bir belgeyi baskı önizlemede görüntülemek için

1. <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A>Sınıfının yöntemini çağırın <xref:Microsoft.Office.Tools.Word.Document> . Bu kod örneğini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>PrintPreview özelliğini ayarlayarak bir belgeyi baskı önizlemede görüntülemek için

1. <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> <xref:Microsoft.Office.Interop.Word.Application> Nesnesinin özelliğini **true**olarak ayarlayın.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>VSTO eklentileri yordamları

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>PrintPreview yöntemini çağırarak bir belgeyi baskı önizlemede görüntülemek için

1. Önizlemek istediğiniz <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> öğesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> . Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>PrintPreview özelliğini ayarlayarak bir belgeyi baskı önizlemede görüntülemek için

1. <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> <xref:Microsoft.Office.Interop.Word.Application> Nesnesinin özelliğini **true**olarak ayarlayın.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)
- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
