---
title: 'Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme'
description: Visual Studio kullanarak program aracılığıyla bir Microsoft Word belgesine nasıl metin ekleyebileceğiniz hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827363"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme
  Microsoft Office Word belgelerine metin eklemenin üç temel yolu vardır:

- Bir aralığa metin ekleyin.

- Bir aralıktaki metni yeni metinle değiştirin.

- <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> <xref:Microsoft.Office.Interop.Word.Selection> İmleç veya seçime metin eklemek için bir nesnenin yöntemini kullanın.

> [!NOTE]
> Ayrıca içerik denetimlerine ve yer işaretlerine metin ekleyebilirsiniz. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md) ve [yer işareti denetimi](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Bir aralığa metin ekleme
 Bir <xref:Microsoft.Office.Interop.Word.Range.Text%2A> <xref:Microsoft.Office.Interop.Word.Range> belgeye metin eklemek için nesnesinin özelliğini kullanın.

### <a name="to-insert-text-in-a-range"></a>Bir aralığa metin eklemek için

1. Belgenin başlangıcında bir Aralık belirtin ve metin **Yeni metin** ekleyin.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu kod etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. <xref:Microsoft.Office.Interop.Word.Range>Bir karakterden, ekli metnin uzunluğuna kadar genişletilen nesneyi seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Bir aralıktaki metni değiştirme
 Belirtilen Aralık metin içeriyorsa, aralıktaki tüm metin, girilen metinle birlikte değişir.

### <a name="to-replace-text-in-a-range"></a>Bir aralıktaki metni değiştirmek için

1. <xref:Microsoft.Office.Interop.Word.Range>Belgedeki ilk 12 karakterden oluşan bir nesne oluşturun.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu kod etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Bu karakterleri dize **yeni metinle** değiştirin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Aralığı seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>TypeText kullanarak metin ekleme
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>Yöntemi, Seçime metin ekler. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> kullanıcının bilgisayarında ayarlanan seçeneklere bağlı olarak farklı davranır. Aşağıdaki yordamdaki kod bir <xref:Microsoft.Office.Interop.Word.Selection> nesne değişkeni bildirir ve açıksa **üzerine yazma** seçeneğini kapatır. **Üzerine yazma** seçeneği etkinleştirilirse, imlecin yanındaki tüm metinlerin üzerine yazılır.

### <a name="to-insert-text-using-the-typetext-method"></a>TypeText yöntemini kullanarak metin eklemek için

1. Bir <xref:Microsoft.Office.Interop.Word.Selection> nesne değişkeni bildirin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Açıksa **üzerine yazma** seçeneğini kapatın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Geçerli seçimin bir ekleme noktası olup olmadığını görmek için test edin.

    Eğer ise, kod kullanarak bir tümce <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> ve sonra yöntemi kullanılarak bir paragraf işareti eklenir <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Seçimin normal bir seçim olup olmadığını görmek için **ElseIf** blok içindeki kod. Eğer ise, **ReplaceSelection** seçeneğinin açık olup olmadığını görmek için engelle ' yi **seçerseniz** , başka bir durumda. Eğer ise, kod <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> Seçili metin bloğunun başlangıcında seçimi bir ekleme noktasına daraltmak için seçimin yöntemini kullanır. Metni ve paragraf işaretini ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Seçim bir ekleme noktası veya seçili metin bloğu değilse, **Else** bloğundaki kod hiçbir şey yapmaz.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Ayrıca, <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> klavyenizde **geri al** tuşunun işlevlerini taklit eden nesnenin yöntemini de kullanabilirsiniz. Ancak, metin ekleme ve düzenleme için olduğunda <xref:Microsoft.Office.Interop.Word.Range> nesnesi size daha fazla denetim sağlar.

   Aşağıdaki örnek, tüm kodu gösterir. Bu örneği kullanmak için, `ThisDocument` projenizdeki veya sınıfından kodu çalıştırın `ThisAddIn` .

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
