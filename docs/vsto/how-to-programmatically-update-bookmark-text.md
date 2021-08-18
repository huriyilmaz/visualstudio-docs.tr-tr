---
title: 'Nasıl güncelleştirmesi: Yer işareti metnini program aracılığıyla güncelleştirme'
description: Visual Studio belgesinde yer tutucu yer işaretine program aracılığıyla metin eklemek için Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2e1c944b00f2581e62f49c56d946d78daefff935
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155687"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Nasıl güncelleştirmesi: Yer işareti metnini program aracılığıyla güncelleştirme
  Word belgesinde yer tutucu yer işaretine metin Microsoft Office, böylece metni daha sonra alabilir veya bir yer işaretinde metin değiştirebilirsiniz. Belge düzeyinde özelleştirme geliştiriyorsanız, verilere bağlı bir denetimde <xref:Microsoft.Office.Tools.Word.Bookmark> metni de güncelleştirebilirsiniz. Daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Yer işareti nesnesi iki türden biri olabilir:

- Bir <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimi.

   <xref:Microsoft.Office.Tools.Word.Bookmark> denetimler, <xref:Microsoft.Office.Interop.Word.Bookmark> veri bağlamayı etkinleştirerek ve olayları ortaya çıkararak yerel nesneleri genişleter. Konak denetimleri hakkında daha fazla bilgi için bkz. [Konak öğeleri ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

- Yerel <xref:Microsoft.Office.Interop.Word.Bookmark> bir nesne.

   <xref:Microsoft.Office.Interop.Word.Bookmark> nesnelerin olayları veya veri bağlama özellikleri yoktur.

  Bir yer işaretine metin atadığınız zaman davranış ile arasında <xref:Microsoft.Office.Interop.Word.Bookmark> farklılık <xref:Microsoft.Office.Tools.Word.Bookmark> gösterir. Daha fazla bilgi için bkz. [Yer işareti denetimi.](../vsto/bookmark-control.md)

## <a name="use-host-controls"></a>Konak denetimlerini kullanma

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Yer işareti denetimi kullanarak yer işareti içeriğini güncelleştirmek için

1. Yer işaretinin adı için `bookmark` bağımsız değişken alan bir yordam ve özelliğine atanma dizesi için bir bağımsız değişken `newText` <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> oluşturun.

    > [!NOTE]
    > Denetimin veya <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> özelliğine metin <xref:Microsoft.Office.Tools.Word.Bookmark> atamak, yer işaretinin silinmesine neden olmaz.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. *newText dizesini* <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> özelliğinin özelliğine attayabilirsiniz. <xref:Microsoft.Office.Tools.Word.Bookmark>

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Word nesnelerini kullanma

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Word Bookmark nesnesi kullanarak yer işareti içeriğini güncelleştirmek için

1. adı için bağımsız değişkeni olan bir yordam ve yer işaretinin özelliğine atanan dize `bookmark` için bir bağımsız değişken <xref:Microsoft.Office.Interop.Word.Bookmark> `newText` <xref:Microsoft.Office.Interop.Word.Range.Text%2A> oluşturun.

    > [!NOTE]
    > Yerel bir Word nesnesine metin atamak <xref:Microsoft.Office.Interop.Word.Bookmark> yer işaretinin silinmesine neden olur.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. *newText dizesini* yer <xref:Microsoft.Office.Interop.Word.Range.Text%2A> işaretinin özelliğine atarak yer işaretini otomatik olarak siler. Ardından yer işaretini koleksiyona yeniden <xref:Microsoft.Office.Interop.Word.Bookmarks> ekleyin.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmede kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
