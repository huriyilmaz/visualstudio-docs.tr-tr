---
title: Belgelerde program aracılığıyla metin bulma ve değiştirme
description: Visual Studio belgesinde program aracılığıyla metin aramak ve değiştirmek için Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: efd725b094ac720f954a0075093ed683e965674d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633913"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Nasıl kullanılır: Belgelerde program aracılığıyla metin arama ve değiştirme
  nesnesi hem hem de nesnelerinin üyesidir ve Word belgelerinden herhangi birini kullanarak word <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> belgesinde metin Microsoft Office kullanabilirsiniz. replace komutu, bul komutunun bir uzantısıdır.

 Microsoft Office Word belgesinde döngü yapmak ve belirli bir metin, biçimlendirme veya stil aramak için bir nesnesi kullanın ve bulunan öğelerin herhangi birini değiştirmek için <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> özelliğini kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Seçim nesnesi kullanma
 Metin bulmak için <xref:Microsoft.Office.Interop.Word.Selection> bir nesnesi kullanırken, belirttiğiniz tüm arama ölçütleri yalnızca o anda seçili olan metne uygulanır. bir <xref:Microsoft.Office.Interop.Word.Selection> ekleme noktası ise belge aranır. Arama ölçütleriyle eşleşen öğe bulunca otomatik olarak seçilir.

 Ölçütlerin birikmeli olduğunu, yani önceki arama ölçütlerine <xref:Microsoft.Office.Interop.Word.Find> ölçüt ekli olduğunu unutmayın. Aramadan önce yöntemini kullanarak önceki <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> aramalardan biçimlendirmeyi temizleme.

### <a name="to-find-text-using-a-selection-object"></a>Seçim nesnesi kullanarak metin bulmak için

1. Bir değişkene arama dizesi atama.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Önceki aramalardan biçimlendirmeyi temizleme.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Arama gerçekleştirin ve sonuçlarla birlikte bir ileti kutusu görüntüleniyor.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   Aşağıdaki örnek, tam yöntemini gösterir.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Range nesnesi kullanma
 Nesne <xref:Microsoft.Office.Interop.Word.Range> kullanmak, kullanıcı arabiriminde herhangi bir şey görüntülemeden metin aramanızı sağlar. <xref:Microsoft.Office.Interop.Word.Find>Nesne,  arama ölçütleriyle eşleşen metin bulunursa True, eşleşmezse **False** döndürür. Ayrıca, metin <xref:Microsoft.Office.Interop.Word.Range> bulunursa, nesneyi arama ölçütleriyle eş olacak şekilde yeniden tanımlar.

### <a name="to-find-text-using-a-range-object"></a>Range nesnesi kullanarak metin bulmak için

1. Belgenin <xref:Microsoft.Office.Interop.Word.Range> ikinci paragrafı oluşan bir nesne tanımlayın.

    Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. nesnesinin <xref:Microsoft.Office.Interop.Word.Range.Find%2A> özelliğini <xref:Microsoft.Office.Interop.Word.Range> kullanarak, önce mevcut biçimlendirme seçeneklerini silin ve sonra beni bul **dizesini arayın.**

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Aramanın sonuçlarını bir ileti kutusunda görüntüler ve görünür hale <xref:Microsoft.Office.Interop.Word.Range> yapmak için öğesini seçin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Arama başarısız olursa ikinci paragraf seçilir; başarılı olursa arama ölçütleri görüntülenir.

   Aşağıdaki örnek, belge düzeyinde özelleştirmenin tam kodunu gösterir. Bu örneği kullanmak için projenizin `ThisDocument` sınıfından kodu çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   Aşağıdaki örnek, bir eklentinin VSTO gösterir. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından kodu çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Belgelerde metin arama ve değiştirme
 Aşağıdaki kod geçerli seçimi arar ve beni bulu dizenin tüm oluşumlarını **Bulundu** dizesiyle **değiştirir.**

### <a name="to-search-for-and-replace-text-in-documents"></a>Belgelerde metin aramak ve değiştirmek için

1. Aşağıdaki örnek kodu projenizin `ThisDocument` or `ThisAddIn` sınıfına ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     sınıfının <xref:Microsoft.Office.Interop.Word.Find> bir yöntemi ve sınıfının da kendi yöntemi <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> <xref:Microsoft.Office.Interop.Word.Replacement> <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> vardır. Bul ve değiştir işlemleri gerçekleştirerek her iki nesne için de ClearFormatting yöntemini kullanabilirsiniz. Bunu yalnızca nesnesinde <xref:Microsoft.Office.Interop.Word.Find> kullanırsanız, değiştirme metninde beklentisiz sonuçlar elde edersiniz.

2. Bulunan <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> her öğeyi değiştirmek <xref:Microsoft.Office.Interop.Word.Find> için nesnesinin yöntemini kullanın. Değiştirilen öğeleri belirtmek için *Replace parametresini* kullanın. Bu parametre aşağıdaki değerlerden biri <xref:Microsoft.Office.Interop.Word.WdReplace> olabilir:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> bulunan tüm öğeleri değiştirir.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> bulunan öğelerin hiçbirinin yerini değiştirmez.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> , bulunan ilk öğeyi değiştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapabilirsiniz: Word'de arama seçeneklerini program aracılığıyla ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
