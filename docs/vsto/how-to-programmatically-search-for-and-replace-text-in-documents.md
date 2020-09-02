---
title: Belgelerde program aracılığıyla metin bulma ve değiştirme
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18a50d6d4ef52a0c50be0b72b4cab5706da4e2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547049"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme
  <xref:Microsoft.Office.Interop.Word.Find>Nesnesi hem hem de nesnelerinin bir üyesidir <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> ve Microsoft Office Word belgelerinde metin aramak için bunlardan birini kullanabilirsiniz. Replace komutu Find komutunun bir uzantısıdır.

 Bir <xref:Microsoft.Office.Interop.Word.Find> Microsoft Office Word belgesi aracılığıyla döngü gerçekleştirmek ve belirli metin, biçimlendirme veya stil aramak için bir nesne kullanın ve <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> bulunan herhangi bir öğeyi değiştirmek için özelliğini kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Seçim nesnesi kullanma
 <xref:Microsoft.Office.Interop.Word.Selection>Metin bulmak için bir nesne kullandığınızda belirttiğiniz tüm arama kriterleri yalnızca seçili metinlere karşı uygulanır. <xref:Microsoft.Office.Interop.Word.Selection>Bir ekleme noktasıdır, belge aranır. Öğe, arama ölçütleriyle eşleşen bulunduğunda otomatik olarak seçilir.

 <xref:Microsoft.Office.Interop.Word.Find>Ölçütlerin birikimli olduğunu ve bu ölçütlerin önceki arama ölçütlerine eklendiğine dikkat etmek önemlidir. Aramadan önce yöntemini kullanarak önceki aramalardan biçimlendirmeyi temizleyin <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> .

### <a name="to-find-text-using-a-selection-object"></a>Bir seçim nesnesi kullanarak metin bulmak için

1. Bir değişkene arama dizesi atayın.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Önceki aramalardan biçimlendirmeyi temizle.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Aramayı yürütün ve sonuçlarla birlikte bir ileti kutusu görüntüleyin.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   Aşağıdaki örnek, tüm yöntemi gösterir.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Aralık nesnesi kullanma
 Bir <xref:Microsoft.Office.Interop.Word.Range> nesne kullanmak, Kullanıcı arabiriminde herhangi bir şey görüntülemeden metin aramanızı sağlar. <xref:Microsoft.Office.Interop.Word.Find>Nesne, arama ölçütleriyle eşleşen metin bulunursa **true** , değilse **false** döndürür. Ayrıca, <xref:Microsoft.Office.Interop.Word.Range> metin bulunursa nesneyi arama ölçütleriyle eşleşecek şekilde yeniden tanımlar.

### <a name="to-find-text-using-a-range-object"></a>Bir Aralık nesnesi kullanarak metin bulmak için

1. <xref:Microsoft.Office.Interop.Word.Range>Belgenin ikinci paragrafından oluşan bir nesne tanımlayın.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. <xref:Microsoft.Office.Interop.Word.Range.Find%2A>Nesnesinin özelliğini kullanarak <xref:Microsoft.Office.Interop.Word.Range> , önce var olan biçimlendirme seçeneklerini temizleyin ve ardından **Find beni bul**dizesini arayın.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Arama sonuçlarını bir ileti kutusunda görüntüleyin ve öğesini seçerek <xref:Microsoft.Office.Interop.Word.Range> görünür hale getirin.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Arama başarısız olursa ikinci paragraf seçilir; başarılı olursa arama ölçütleri görüntülenir.

   Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam kodu gösterir. Bu örneği kullanmak için, `ThisDocument` projenizdeki sınıfından kodu çalıştırın.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   Aşağıdaki örnek, bir VSTO eklentisi için tam kodu gösterir. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından kodu çalıştırın.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Belgelerde metin ara ve Değiştir
 Aşağıdaki kod, geçerli seçimi arar ve dize **bul** 'un tüm tekrarlarının **bulduğu**dize ile yerini alır.

### <a name="to-search-for-and-replace-text-in-documents"></a>Belgelerde metin aramak ve değiştirmek için

1. Aşağıdaki örnek kodu `ThisDocument` `ThisAddIn` projenizdeki or sınıfına ekleyin.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     <xref:Microsoft.Office.Interop.Word.Find>Sınıfında bir yöntemi vardır <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> ve <xref:Microsoft.Office.Interop.Word.Replacement> sınıfın kendi yöntemi de vardır <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> . Bulma ve değiştirme işlemlerini gerçekleştirirken, her iki nesnenin de ClearFormatting yöntemini kullanmanız gerekir. Bunu yalnızca nesne üzerinde kullanırsanız <xref:Microsoft.Office.Interop.Word.Find> , değiştirme metninde beklenmeyen sonuçlar elde edebilirsiniz.

2. <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> <xref:Microsoft.Office.Interop.Word.Find> Bulunan her öğeyi değiştirmek için nesnesinin yöntemini kullanın. Hangi öğelerin yerini belirlemek için *Replace* parametresini kullanın. Bu parametre aşağıdaki değerlerden biri olabilir <xref:Microsoft.Office.Interop.Word.WdReplace> :

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> bulunan tüm öğeleri değiştirir.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> bulunan öğelerin hiçbirini değiştirir.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> bulunan ilk öğeyi değiştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
