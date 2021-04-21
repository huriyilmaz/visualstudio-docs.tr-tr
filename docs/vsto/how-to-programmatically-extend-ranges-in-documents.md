---
title: 'Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme'
description: Belge düzeyinde veya uygulama düzeyinde bir Microsoft Word belgesindeki başlangıç ve bitiş noktası aralıklarını programlı bir şekilde nasıl genişletebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a539bbbc4ad8d73477e660ef9903ac51dce712f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826531"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme
  Bir <xref:Microsoft.Office.Interop.Word.Range> Microsoft Office Word belgesinde bir nesne tanımladıktan sonra, ve yöntemlerini kullanarak başlangıç ve bitiş noktalarını değiştirirsiniz <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>Ve <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> yöntemleri aynı iki bağımsız değişkeni, *birimi* ve *sayıyı* alır. *Count* bağımsız değişkeni, taşınacak birim sayısı ve *birim* bağımsız değişkeni aşağıdaki değerlerden biri olabilir <xref:Microsoft.Office.Interop.Word.WdUnits> :

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  Aşağıdaki örnek yedi karakterlik bir aralığı tanımlar. Daha sonra aralığın başlangıç konumunu orijinal başlangıç konumundan sonra yedi karakter olarak kaydırır. Aralığın bitiş konumu başlangıç konumundan sonra da yedi karakter olduğundan, sonuç sıfır karakterden oluşan bir aralıktır. Daha sonra kod, son konumu geçerli bitiş konumundan sonra yedi karakteri taşımaktır.

## <a name="to-extend-a-range"></a>Bir aralığı genişletmek için

1. Bir karakter aralığı tanımlayın. Daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla aralıkları tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> <xref:Microsoft.Office.Interop.Word.Range> Aralığın başlangıç konumunu taşımak için nesnesinin yöntemini kullanın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> <xref:Microsoft.Office.Interop.Word.Range> Aralığın bitiş konumunu taşımak için nesnesinin yöntemini kullanın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>Belge düzeyi özelleştirme kodu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki bir aralığı genişletmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam kodu gösterir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>VSTO eklenti kodu

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Uygulama düzeyi VSTO eklentideki bir aralığı genişletmek için

1. Aşağıdaki örnek, bir VSTO eklentisi için tam kodu gösterir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
