---
title: 'Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma'
description: Visual Studio kullanarak bir Microsoft Word belgesinde bulunan öğeler aracılığıyla programlı bir şekilde nasıl dolaşkullanabileceğinizi öğrenin.
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
ms.openlocfilehash: ab13fee63ab9ed98ba75148a8f099fe1df003bef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083227"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma
  <xref:Microsoft.Office.Interop.Word.Find>Sınıfında <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , Aranan öğe bulunduğunda **true değeri** döndüren bir özelliği vardır. Yöntemini kullanarak içinde bulunan tüm örnekleri içinde döngü yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Bulunan öğeler arasında döngü uygulamak için

1. Bir <xref:Microsoft.Office.Interop.Word.Range> nesne bildirin.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. <xref:Microsoft.Office.Interop.Word.Find.Found%2A>Belgedeki dizeyi tüm tekrarlamalarını aramak için döngüsünde özelliğini kullanın ve dize her bulunduğunda tamsayı değişkenini 1 artırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Bir ileti kutusunda dizenin kaç kez bulunmuştur görüntüleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   Aşağıdaki örneklerde, tamamlanmış yöntemi gösterilmektedir.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki öğeler arasında döngü gerçekleştirmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam kodu gösterir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>VSTO eklentideki öğeler arasında döngü uygulamak için

1. aşağıdaki örnek, bir VSTO eklentisi için tam kodu gösterir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde yeniden metin arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
