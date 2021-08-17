---
title: 'Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme'
description: Aralık nesnesini kullanarak program aracılığıyla bir belge Microsoft Word aralık tanımlamayı ve seçmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 98b7e6aa0d95322fb3a69263d487ba0ce21e5d9f5c7c8b4606c12cbdd489655d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394473"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme
  Bir nesne kullanarak word belgesinde Microsoft Office <xref:Microsoft.Office.Interop.Word.Range> tanımlayabilirsiniz. Örneğin, nesnenin yöntemini kullanarak veya sınıfın Content özelliğini (belge düzeyi özelleştirmede) ya da sınıfını (bir VSTO Eklentisinde) kullanarak belgenin tamamını çeşitli <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> yollarla <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> seçebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Aralık tanımlama
 Aşağıdaki örnekte, etkin belgedeki ilk yedi karakteri içeren, yazdırilmeyen karakterler de dahil olmak üzere <xref:Microsoft.Office.Interop.Word.Range> yeni bir nesnenin nasıl oluşturulmakta olduğu gösterir. Ardından aralık içindeki metni seçer.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede bir aralık tanımlamak için

1. sınıfının yöntemine bir başlangıç ve bitiş karakteri geçerek aralığı <xref:Microsoft.Office.Tools.Word.Document.Range%2A> belgeye <xref:Microsoft.Office.Tools.Word.Document> ekleyin. Bu kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Bir eklentiyi kullanarak bir VSTO tanımlamak için

1. sınıfının yöntemine bir başlangıç ve bitiş karakteri geçerek aralığı <xref:Microsoft.Office.Interop.Word._Document.Range%2A> belgeye <xref:Microsoft.Office.Interop.Word.Document> ekleyin. Aşağıdaki kod örneği, etkin belgeye bir aralık ekler. Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesinde bir aralık seçme
 Aşağıdaki örneklerde, bir nesnenin yöntemini kullanarak veya sınıfının özelliği kullanılarak belgenin tamamının <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> nasıl <xref:Microsoft.Office.Tools.Word.Document.Content%2A> seçkili olduğu <xref:Microsoft.Office.Tools.Word.Document> gösterir.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select yöntemini kullanarak belgenin tamamını aralık olarak seçmek için

1. Belgenin <xref:Microsoft.Office.Interop.Word.Range.Select%2A> tamamını içeren <xref:Microsoft.Office.Interop.Word.Range> bir yöntemini kullanın. Aşağıdaki kod örneğini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>İçerik özelliğini kullanarak belgenin tamamını aralık olarak seçmek için

1. Belgenin <xref:Microsoft.Office.Tools.Word.Document.Content%2A> tamamını kapsayan bir aralık tanımlamak için özelliğini kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   Bir aralığı tanımlamak için diğer nesnelerin yöntemlerini ve özelliklerini de kullanabilirsiniz.

### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgede bir cümle seçmek için

1. Koleksiyonunu kullanarak aralığı <xref:Microsoft.Office.Interop.Word.Sentences> ayarlayın. Seçmek istediğiniz cümlenin dizinini kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   Cümle seçmenin bir diğer yolu da aralığın başlangıç ve bitiş değerlerini el ile ayarlamaktır.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Başlangıç ve bitiş değerlerini el ile ayarerek bir cümle seçmek için

1. Bir aralık değişkeni oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. Belgede en az iki cümle olup olduğunu kontrol edin, aralığın *Başlangıç* *ve* Bitiş bağımsız değişkenlerini ayarlayın ve ardından aralığı seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Bir eklentiyi kullanarak VSTO seçin
 Aşağıdaki örneklerde, bir nesnenin yöntemini kullanarak veya sınıfının özelliği kullanılarak belgenin tamamının <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> nasıl <xref:Microsoft.Office.Interop.Word._Document.Content%2A> seçkili olduğu <xref:Microsoft.Office.Interop.Word.Document> gösterir.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select yöntemini kullanarak belgenin tamamını aralık olarak seçmek için

1. Belgenin <xref:Microsoft.Office.Interop.Word.Range.Select%2A> tamamını içeren <xref:Microsoft.Office.Interop.Word.Range> bir yöntemini kullanın. Aşağıdaki kod örneği etkin belgenin içeriğini seçer. Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>İçerik özelliğini kullanarak belgenin tamamını aralık olarak seçmek için

1. Belgenin <xref:Microsoft.Office.Interop.Word._Document.Content%2A> tamamını kapsayan bir aralık tanımlamak için özelliğini kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   Bir aralığı tanımlamak için diğer nesnelerin yöntemlerini ve özelliklerini de kullanabilirsiniz.

### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgede bir cümle seçmek için

1. Koleksiyonunu kullanarak aralığı <xref:Microsoft.Office.Interop.Word.Sentences> ayarlayın. Seçmek istediğiniz cümlenin dizinini kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   Cümle seçmenin bir diğer yolu da aralığın başlangıç ve bitiş değerlerini el ile ayarlamaktır.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Başlangıç ve bitiş değerlerini el ile ayarerek bir cümle seçmek için

1. Bir aralık değişkeni oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. Belgede en az iki cümle olup olduğunu kontrol edin, aralığın *Başlangıç* *ve* Bitiş bağımsız değişkenlerini ayarlayın ve ardından aralığı seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>Ayrıca bkz.
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl olur: Aralıklarda başlangıç ve bitiş karakterlerini program aracılığıyla alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları veya seçimleri program aracılığıyla daralt](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl edilir: Aralık oluştururken program aracılığıyla paragraf işaretlerini dışlama](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
