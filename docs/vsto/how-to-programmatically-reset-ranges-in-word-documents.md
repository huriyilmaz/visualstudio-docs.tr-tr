---
title: 'Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama'
description: Visual Studio belgesinde var olan bir aralığı program aracılığıyla yeniden boyutlandırmak için Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5aba88ca36443d039487444204de6d437db8300d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726714"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama
  Word <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> belgesinde var olan bir aralığı yeniden boyutlandırmak Microsoft Office kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Mevcut bir aralığı sıfırlamak için

1. Belgedeki ilk yedi karakterden başlayarak bir başlangıç aralığı ayarlayın.

     Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet43":::

     Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu kod etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet43":::

2. İkinci <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> cümlede aralığı başlatmak ve beşinci cümlenin sonunda sona erer.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet44":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet44":::

## <a name="document-level-customization-example"></a>Document-Level Özelleştirme Örneği

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede var olan bir aralığı sıfırlamak için

1. Aşağıdaki örnekte, belge düzeyinde özelleştirmenin tam örneği gösterir. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet42":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Bir eklentide var olan bir VSTO sıfırlamak için

1. Aşağıdaki örnek, bir eklentinin VSTO gösterir. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet42":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıllı: Aralıklarda başlangıç ve bitiş karakterlerini program aracılığıyla alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl kullanılır: Belgelerde aralıkları veya seçimleri program aracılığıyla daralt](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
