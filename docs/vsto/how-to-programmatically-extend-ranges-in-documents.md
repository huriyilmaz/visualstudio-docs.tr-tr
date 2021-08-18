---
title: 'Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme'
description: Belge düzeyinde veya uygulama düzeyinde bir belgede başlangıç ve Microsoft Word aralıklarını program aracılığıyla genişletmeyi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7297a638b22ca031ae4c728675a054a3430a2cf8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148031"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Nasıl kullanılır: Belgelerde aralıkları Program Aracılığıyla Genişletme
  bir Word belgesinde bir Microsoft Office tanımlayarak, ve yöntemlerini kullanarak nesnenin <xref:Microsoft.Office.Interop.Word.Range> başlangıç ve bitiş noktalarını <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> değiştirirsiniz. ve <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> yöntemleri aynı iki bağımsız değişkeni <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> alır: *Unit* ve *Count*. Count *bağımsız* değişkeni taşınan birim sayısıdır ve *Unit* bağımsız değişkeni aşağıdaki değerlerden biri <xref:Microsoft.Office.Interop.Word.WdUnits> olabilir:

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

  Aşağıdaki örnek yedi karakterlik bir aralık tanımlar. Ardından özgün başlangıç konumundan sonraki yedi karakterlik aralığın başlangıç konumunu taşır. Aralığın bitiş konumu da başlangıç konumundan yedi karakter sonra olduğundan, sonuç sıfır karakterden oluşan bir aralıktır. Kod daha sonra bitiş konumunu geçerli bitiş konumundan yedi karakter sonra taşır.

## <a name="to-extend-a-range"></a>Bir aralığı genişletmek için

1. Bir karakter aralığı tanımlayın. Daha fazla bilgi için [bkz. Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme.](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

     Aşağıdaki kod örneği, belge düzeyi özelleştirmede kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     Aşağıdaki kod örneği bir eklentide VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. Aralığın <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> başlangıç <xref:Microsoft.Office.Interop.Word.Range> konumunu taşımak için nesnesinin yöntemini kullanın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. Aralığın <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> bitiş <xref:Microsoft.Office.Interop.Word.Range> konumunu taşımak için nesnesinin yöntemini kullanın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>Belge düzeyi özelleştirme kodu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede aralığı genişletmek için

1. Aşağıdaki örnek, belge düzeyinde özelleştirmenin tam kodunu gösterir. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>VSTO Eklenti Kodu

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Uygulama düzeyinde bir aralığı genişletmek için VSTO ekleme

1. Aşağıdaki örnek, bir eklentinin VSTO gösterir. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları veya seçimleri program aracılığıyla daralt](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl olur: Aralıklarda başlangıç ve bitiş karakterlerini program aracılığıyla alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl edilir: Aralık oluştururken program aracılığıyla paragraf işaretlerini dışlama](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
