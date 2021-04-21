---
title: 'Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme'
description: Visual Studio 'Yu kullanarak bir Microsoft Word belgesindeki yer tutucu yer işaretine metin ekleme hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826206"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme
  Metni daha sonra alabilmeniz veya bir yer işaretinin içindeki metni değiştirmek için Microsoft Office Word belgesinde yer tutucu yer işaretine metin ekleyebilirsiniz. Belge düzeyi özelleştirmesi geliştiriyorsanız, verilere bağlanan bir denetimdeki metni de güncelleştirebilirsiniz <xref:Microsoft.Office.Tools.Word.Bookmark> . Daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Yer işareti nesnesi iki türden biri olabilir:

- Bir <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimi.

   <xref:Microsoft.Office.Tools.Word.Bookmark> denetimler <xref:Microsoft.Office.Interop.Word.Bookmark> , veri bağlamayı etkinleştirerek ve olayları ortaya çıkaran yerel nesneleri genişletir. Konak denetimleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

- Yerel bir <xref:Microsoft.Office.Interop.Word.Bookmark> nesne.

   <xref:Microsoft.Office.Interop.Word.Bookmark> nesneler, olay veya veri bağlama özelliklerine sahip değildir.

  Bir yer işaretine metin atadığınızda, davranış bir ve arasında farklılık gösterir <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.Bookmark> . Daha fazla bilgi için bkz. [Bookmark Control](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Konak denetimlerini kullanma

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Yer işareti içeriğini bir yer işareti denetimi kullanarak güncelleştirmek için

1. `bookmark`Yer işaretinin adı için bir bağımsız değişken alan ve `newText` özelliğine atanacak dize için bir bağımsız değişken alan bir yordam oluşturun <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .

    > [!NOTE]
    > <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> Bir denetimin veya özelliğine metin atama <xref:Microsoft.Office.Tools.Word.Bookmark> , yer işaretinin silinmesine neden olmaz.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. *NewText* dizesini <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> öğesinin özelliğine atayın <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Word nesnelerini kullanma

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Yer işareti içeriğini bir Word Bookmark nesnesi kullanarak güncelleştirmek için

1. `bookmark`Adı için bağımsız değişkenine sahip bir yordam <xref:Microsoft.Office.Interop.Word.Bookmark> ve `newText` yer işaretinin özelliğine atanacak dize için bir bağımsız değişken oluşturun <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

    > [!NOTE]
    > Yerel bir Word nesnesine metin atama <xref:Microsoft.Office.Interop.Word.Bookmark> , yer işaretinin silinmesine neden olur.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. *NewText* dizesini yer işaretinin özelliğine atayın <xref:Microsoft.Office.Interop.Word.Range.Text%2A> ve bu, yer işaretini otomatik olarak siler. Sonra yer işaretini koleksiyona yeniden ekleyin <xref:Microsoft.Office.Interop.Word.Bookmarks> .

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
