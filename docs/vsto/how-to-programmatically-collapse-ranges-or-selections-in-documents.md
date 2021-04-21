---
title: Belgelerdeki aralıkları veya seçimleri program aracılığıyla daraltma
description: Bir Aralık veya seçim nesnesiyle çalışıyorsanız, metin eklemeden önce seçimi bir ekleme noktası olarak değiştirmek isteyebilirsiniz.
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
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828650"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma
  <xref:Microsoft.Office.Interop.Word.Range>Veya <xref:Microsoft.Office.Interop.Word.Selection> nesnesiyle çalışıyorsanız, varolan metnin üzerine yazılmasını önlemek için, metin eklemeden önce seçimi bir ekleme noktasıyla değiştirmek isteyebilirsiniz. Ve nesnelerinin her ikisi de, <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> numaralandırma değerlerini kullanan bir daraltma yöntemine sahiptir <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> :

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> seçimi seçimin başlangıcına daraltır. Bir sabit listesi değeri belirtmezseniz bu varsayılandır.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> seçimi seçimin sonuna daraltır.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Bir aralığı daraltmak ve yeni metin eklemek için

1. <xref:Microsoft.Office.Interop.Word.Range>Belgenin ilk paragrafından oluşan bir nesne oluşturun.

    Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu kod etkin belgeyi kullanır.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart>Aralığı daraltmak için sabit listesi değerini kullanın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Yeni metni ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. <xref:Microsoft.Office.Interop.Word.Range> seçeneğini belirleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>Sabit listesi değerini kullanırsanız, metin aşağıdaki paragrafın başına eklenir.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Yeni bir cümle eklemek, paragraf işaretleyicisinden önce onu ekleyecektir, ancak bu durum, orijinal aralığı paragraf işaretçisini içerdiğinden bu durum değildir. Daha fazla bilgi için bkz. [nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığı daraltmak için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam yöntemi gösterir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>VSTO eklentideki bir aralığı daraltmak için

1. Aşağıdaki örnek, bir VSTO eklentisi için tam yöntemi gösterir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
