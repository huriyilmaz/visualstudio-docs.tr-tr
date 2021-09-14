---
title: 'Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme'
description: Visual Studio kullanarak program aracılığıyla bir Microsoft Word belgeye nasıl metin Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c2acc09b04ba08543faa449788f61f7fa72c8c72
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633926"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme
  Word belgelerine metin eklemenin başlıca Microsoft Office vardır:

- Bir aralıkta metin ekleme.

- Bir aralıkta yer alan metni yeni metinle değiştirin.

- <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>İmleç veya <xref:Microsoft.Office.Interop.Word.Selection> seçime metin eklemek için nesnesinin yöntemini kullanın.

> [!NOTE]
> ayrıca içerik denetimlerine ve yer işaretlerine metin ebilirsiniz. Daha fazla bilgi için [bkz. İçerik denetimleri ve](../vsto/content-controls.md) [Yer işareti denetimi.](../vsto/bookmark-control.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Bir aralıkta metin ekleme
 Belgeye <xref:Microsoft.Office.Interop.Word.Range.Text%2A> metin eklemek için <xref:Microsoft.Office.Interop.Word.Range> nesnesinin özelliğini kullanın.

### <a name="to-insert-text-in-a-range"></a>Bir aralıkta metin eklemek için

1. Bir belgenin başında bir aralık belirtin ve Yeni Metin **metnini ekleyin.**

     Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     Aşağıdaki kod örneği bir eklentide VSTO kullanılabilir. Bu kod etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Bir <xref:Microsoft.Office.Interop.Word.Range> karakterden eklenen metnin uzunluğuna genişletilmiş nesnesini seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Bir aralıkta metin değiştirme
 Belirtilen aralık metin içeriyorsa, aralıkta yer alan tüm metin eklenen metinle değiştirilir.

### <a name="to-replace-text-in-a-range"></a>Bir aralıkta metin değiştirmek için

1. Belgedeki <xref:Microsoft.Office.Interop.Word.Range> ilk 12 karakterden oluşan bir nesne oluşturun.

     Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     Aşağıdaki kod örneği bir eklentide VSTO kullanılabilir. Bu kod etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Bu karakterleri Yeni Metin **dizesiyle değiştirin.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Aralığı seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>TypeText kullanarak metin ekleme
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>yöntemi, seçime metin ekler. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> kullanıcının bilgisayarına ayarlanmış seçeneklere bağlı olarak farklı davranır. Aşağıdaki yordamda yer alan kod bir <xref:Microsoft.Office.Interop.Word.Selection> nesne değişkeni bildirmektedir ve **açıksa Overtype** seçeneğini devre dışıdır. Overtype **seçeneği etkinleştirilirse** imlecin yanındaki herhangi bir metnin üzerine yazılır.

### <a name="to-insert-text-using-the-typetext-method"></a>TypeText yöntemini kullanarak metin eklemek için

1. Bir nesne <xref:Microsoft.Office.Interop.Word.Selection> değişkeni bildir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Açıksa **Overtype** seçeneğini kapatın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Geçerli seçimin ekleme noktası olup olmadığını test edin.

    Varsa, kod kullanarak bir cümle ekler ve <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> ardından yöntemini kullanarak bir paragraf işareti <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. **ElseIf bloğundaki kod,** seçimin normal bir seçim olup olmadığını görmek için testlerini engelleyebilir. Öyleyse, Başka bir **If** engelle testlerinde **ReplaceSelection** seçeneğinin açık olup olmadığını kontrol etmek için. Varsa kod, seçimi seçilen metin bloğun başındaki ekleme noktasına daraltan <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> seçim yöntemini kullanır. Metni ve paragraf işaretini ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Seçim bir ekleme noktası veya seçili metin bloğu değilse Else bloğundaki kod **hiçbir** şey yapmadı.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Klavyenizde Geri Al tuşu işlevselliğini taklit eden nesnesinin <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> **yöntemini** de kullanabilirsiniz. Ancak, metin ekleme ve değiştirme söz konusu olduğunda nesne size <xref:Microsoft.Office.Interop.Word.Range> daha fazla denetim sunar.

   Aşağıdaki örnekte kodun tamamlanmıştır. Bu örneği kullanmak için projenizin or `ThisDocument` `ThisAddIn` sınıfından kodu çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde program aracılığıyla metin biçimlendirme](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
