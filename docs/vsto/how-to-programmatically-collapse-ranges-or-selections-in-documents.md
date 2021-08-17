---
title: Program aracılığıyla belgelerde aralıkları veya seçimleri daralt
description: Bir Aralık veya Seçim nesnesiyle çalışıyorsanız, metin eklemeden önce seçimi ekleme noktası olarak değiştirmek gerektirebilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 18923a8db119540685ba2292c99082e00dabafd15e1888af13305f2b6c209588
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394491"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Nasıl kullanılır: Belgelerde aralıkları veya seçimleri program aracılığıyla daralt
  Bir veya nesnesiyle çalışıyorsanız, var olan metnin üzerine yazmamak için, metin eklemeden önce seçimi ekleme noktası <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> olarak değiştirmek iyi olabilir. Ve <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> nesnelerinin her ikisi de, numaralama değerlerini kullanan bir <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> Daralt yöntemine sahiptir:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> seçimi, seçimin başına daraltıyor. Bir numaralama değeri belirtmezseniz bu varsayılan değerdir.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> seçimi, seçimin sonuna daraltıyor.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Bir aralığı daraltarak yeni metin eklemek için

1. Belgenin <xref:Microsoft.Office.Interop.Word.Range> ilk paragrafı oluşan bir nesnesi oluşturun.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmede kullanılabilir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu kod etkin belgeyi kullanır.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Aralığı <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> daraltan bir numaralama değeri kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Yeni metni ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. <xref:Microsoft.Office.Interop.Word.Range> seçeneğini belirleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Numaralama <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> değerini kullanırsanız, metin aşağıdaki paragrafın başına eklenir.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Yeni bir cümle eklemenin bunu paragraf işaretçisine eklemesini bekliyor olabilirsiniz, ancak özgün aralık paragraf işaretçisini dahil olduğundan bu durum geçerli değildir. Daha fazla bilgi için [bkz. Nasıl oluşturulur: Aralık oluştururken paragraf işaretlerini program aracılığıyla dışlama.](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede bir aralığı daralt

1. Aşağıdaki örnekte, belge düzeyinde özelleştirmenin tam yöntemi gösterir. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Bir eklentide bir aralığı VSTO için

1. Aşağıdaki örnek, bir eklentinin VSTO gösterir. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl olur: Aralıklarda başlangıç ve bitiş karakterlerini program aracılığıyla alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl edilir: Aralık oluştururken program aracılığıyla paragraf işaretlerini dışlama](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
