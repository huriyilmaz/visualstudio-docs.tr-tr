---
title: 'Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü'
description: Visual Studio kullanarak bir belgedeki bulunan öğelerde programlı Microsoft Word döngü Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8a9333efec2886ba4ed7d8d33a99e2de85bd1733f10837299643cae0c19a9f30
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440753"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü
  sınıfının, <xref:Microsoft.Office.Interop.Word.Find> aranan <xref:Microsoft.Office.Interop.Word.Find.Found%2A> öğe her **bulunsa true** döndüren bir özelliği vardır. içinde bulunan tüm örneklerde döngü için yöntemini <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Bulunan öğelerde döngü yapmak için

1. Bir nesnesi <xref:Microsoft.Office.Interop.Word.Range> bildir.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmede kullanılabilir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    Aşağıdaki kod örneği bir eklentide VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Belgede dizenin tüm oluşumlarını aramak için bir döngüde özelliğini kullanın ve dize her bulunurken bir tamsayı değişkenlerini <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 1 artırabilirsiniz.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. İleti kutusunda dizenin kaç kez bulun olduğunu görüntüler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   Aşağıdaki örneklerde yöntemin tamamlanmıştır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Belge düzeyi özelleştirmedeki öğelerde döngü yapmak için

1. Aşağıdaki örnekte, belge düzeyinde özelleştirmenin tam kodu gösterir. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Bir eklentideki öğelerde döngü VSTO için

1. Aşağıdaki örnek, bir eklentinin VSTO gösterir. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapabilirsiniz: Word'de arama seçeneklerini program aracılığıyla ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
