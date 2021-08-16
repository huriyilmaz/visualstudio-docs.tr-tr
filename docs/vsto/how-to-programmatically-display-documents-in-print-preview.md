---
title: "Nasıl kullanılır: Baskı Önizleme'de program aracılığıyla belgeleri görüntüleme"
description: Belgelerde belge görüntülemeyi program aracılığıyla Baskı Önizleme'de Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 855aea5fefede1e454a8f273ad1cdf402cae4b9aea6159f0ac6f86fb93d64818
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366244"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Nasıl kullanılır: Baskı Önizleme'de program aracılığıyla belgeleri görüntüleme
  Çözümünüz bir rapor üretirse, raporu kullanıcıya Baskı Önizleme modunda görüntülemek istiyor olabilir.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Belge düzeyinde özelleştirme yordamları

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>PrintPreview yöntemini çağırarak Bir belgeyi Print Preview'da görüntülemek için

1. sınıfının <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> yöntemini <xref:Microsoft.Office.Tools.Word.Document> çağırma. Bu kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>PrintPreview özelliğini ayarerek Bir belgeyi Baskı Önizlemesinde görüntülemek için

1. nesnesinin <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> özelliğini <xref:Microsoft.Office.Interop.Word.Application> true olarak **ayarlayın.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>VSTO Yordamları

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>PrintPreview yöntemini çağırarak Bir belgeyi Print Preview'da görüntülemek için

1. Önizlemek <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> istediğiniz <xref:Microsoft.Office.Interop.Word.Document> yöntemini çağırma. Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>PrintPreview özelliğini ayarerek Bir belgeyi Baskı Önizlemesinde görüntülemek için

1. nesnesinin <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> özelliğini <xref:Microsoft.Office.Interop.Word.Application> true olarak **ayarlayın.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)
- [Nasıl kullanılır: Mevcut belgeleri program aracılığıyla açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
