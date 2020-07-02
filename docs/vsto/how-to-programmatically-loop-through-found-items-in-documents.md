---
title: 'Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e200f910e002bb9380bd5a1b556dc6f1cab08810
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544748"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma
  <xref:Microsoft.Office.Interop.Word.Find>Sınıfında <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , Aranan öğe bulunduğunda **true değeri** döndüren bir özelliği vardır. Yöntemini kullanarak içinde bulunan tüm örnekleri içinde döngü yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Bulunan öğeler arasında döngü uygulamak için

1. Bir <xref:Microsoft.Office.Interop.Word.Range> nesne bildirin.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. <xref:Microsoft.Office.Interop.Word.Find.Found%2A>Belgedeki dizeyi tüm tekrarlamalarını aramak için döngüsünde özelliğini kullanın ve dize her bulunduğunda tamsayı değişkenini 1 artırın.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. Bir ileti kutusunda dizenin kaç kez bulunmuştur görüntüleyin.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   Aşağıdaki örneklerde, tamamlanmış yöntemi gösterilmektedir.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki öğeler arasında döngü gerçekleştirmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam kodu gösterir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>VSTO eklentideki öğeler arasında döngü uygulamak için

1. Aşağıdaki örnek, bir VSTO eklentisi için tam kodu gösterir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde yeniden metin arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
