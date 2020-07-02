---
title: 'Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5af4ceeb37574fef6eb55d80f3c173b71ac090e0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545957"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme
  Bir nesne kullanarak Microsoft Office Word belgesinde bir Aralık tanımlayabilirsiniz <xref:Microsoft.Office.Interop.Word.Range> . Tüm belgeyi, örneğin, <xref:Microsoft.Office.Interop.Word.Range.Select%2A> nesnesinin yöntemini kullanarak <xref:Microsoft.Office.Interop.Word.Range> veya sınıfının içerik özelliğini <xref:Microsoft.Office.Tools.Word.Document> (belge düzeyi özelleştirmesinde) ya da <xref:Microsoft.Office.Interop.Word.Document> sınıfını (VSTO eklentisi içinde) kullanarak seçebilirsiniz (örneğin, nesne).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Bir Aralık tanımlayın
 Aşağıdaki örnek, <xref:Microsoft.Office.Interop.Word.Range> yazdırılmayan karakterler de dahil olmak üzere etkin belgedeki ilk yedi karakteri içeren yeni bir nesne oluşturmayı gösterir. Sonra Aralık içindeki metni seçer.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığı tanımlamak için

1. Sınıf yöntemine bir başlangıç ve bitiş karakteri geçirerek belgeye aralığı ekleyin <xref:Microsoft.Office.Tools.Word.Document.Range%2A> <xref:Microsoft.Office.Tools.Word.Document> . Bu kod örneğini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>VSTO eklentisini kullanarak bir Aralık tanımlamak için

1. Sınıf yöntemine bir başlangıç ve bitiş karakteri geçirerek belgeye aralığı ekleyin <xref:Microsoft.Office.Interop.Word._Document.Range%2A> <xref:Microsoft.Office.Interop.Word.Document> . Aşağıdaki kod örneği, etkin belgeye bir Aralık ekler. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir Aralık seçin
 Aşağıdaki örneklerde <xref:Microsoft.Office.Interop.Word.Range.Select%2A> , bir nesnenin yöntemini kullanarak <xref:Microsoft.Office.Interop.Word.Range> veya <xref:Microsoft.Office.Tools.Word.Document.Content%2A> sınıfının özelliğini kullanarak belgenin tamamını seçme gösterilmektedir <xref:Microsoft.Office.Tools.Word.Document> .

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select metodunu kullanarak tüm belgeyi bir Aralık olarak seçmek için

1. <xref:Microsoft.Office.Interop.Word.Range.Select%2A>Tüm belgeyi içeren bir öğesinin yöntemini kullanın <xref:Microsoft.Office.Interop.Word.Range> . Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Içerik özelliğini kullanarak tüm belgeyi bir Aralık olarak seçmek için

1. <xref:Microsoft.Office.Tools.Word.Document.Content%2A>Tüm belgeyi kapsayan bir Aralık tanımlamak için özelliğini kullanın.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   Bir Aralık tanımlamak için diğer nesnelerin yöntemlerini ve özelliklerini de kullanabilirsiniz.

### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgede bir cümle seçmek için

1. Koleksiyonu kullanarak aralığı ayarlayın <xref:Microsoft.Office.Interop.Word.Sentences> . Seçmek istediğiniz tümcenin dizinini kullanın.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Tümceyi seçmek için bir diğer yol ise aralığın başlangıç ve bitiş değerlerini el ile ayarlamanıza yöneliktir.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Başlangıç ve bitiş değerlerini el ile ayarlayarak bir tümceyi seçmek için

1. Aralık değişkeni oluşturun.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. Belgede en az iki cümle olup olmadığını denetleyin, aralığın *Başlangıç* ve *bitiş* bağımsız değişkenlerini ayarlayıp aralığı seçin.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>VSTO eklentisi kullanarak bir Aralık seçin
 Aşağıdaki örneklerde <xref:Microsoft.Office.Interop.Word.Range.Select%2A> , bir nesnenin yöntemini kullanarak <xref:Microsoft.Office.Interop.Word.Range> veya <xref:Microsoft.Office.Interop.Word._Document.Content%2A> sınıfının özelliğini kullanarak belgenin tamamını seçme gösterilmektedir <xref:Microsoft.Office.Interop.Word.Document> .

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select metodunu kullanarak tüm belgeyi bir Aralık olarak seçmek için

1. <xref:Microsoft.Office.Interop.Word.Range.Select%2A>Tüm belgeyi içeren bir öğesinin yöntemini kullanın <xref:Microsoft.Office.Interop.Word.Range> . Aşağıdaki kod örneği etkin belgenin içeriğini seçer. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Içerik özelliğini kullanarak tüm belgeyi bir Aralık olarak seçmek için

1. <xref:Microsoft.Office.Interop.Word._Document.Content%2A>Tüm belgeyi kapsayan bir Aralık tanımlamak için özelliğini kullanın.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   Bir Aralık tanımlamak için diğer nesnelerin yöntemlerini ve özelliklerini de kullanabilirsiniz.

### <a name="to-select-a-sentence-in-the-active-document"></a>Etkin belgede bir cümle seçmek için

1. Koleksiyonu kullanarak aralığı ayarlayın <xref:Microsoft.Office.Interop.Word.Sentences> . Seçmek istediğiniz tümcenin dizinini kullanın.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Tümceyi seçmek için bir diğer yol ise aralığın başlangıç ve bitiş değerlerini el ile ayarlamanıza yöneliktir.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Başlangıç ve bitiş değerlerini el ile ayarlayarak bir tümceyi seçmek için

1. Aralık değişkeni oluşturun.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. Belgede en az iki cümle olup olmadığını denetleyin, aralığın *Başlangıç* ve *bitiş* bağımsız değişkenlerini ayarlayıp aralığı seçin.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Ayrıca bkz.
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
