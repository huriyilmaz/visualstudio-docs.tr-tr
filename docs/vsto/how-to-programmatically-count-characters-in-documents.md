---
title: 'Nasıl yapılır: belgelerde program aracılığıyla karakter sayma'
description: Karakter koleksiyonunun Count özelliğini kullanarak bir belgedeki karakter sayısını nasıl belirleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824016"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Nasıl yapılır: belgelerde program aracılığıyla karakter sayma
  Belgedeki ilk karakter, ekleme noktasını temsil eden 0 karakter konumunda bulunur. Son karakter konumu belgedeki toplam karakter sayısına eşittir. Bir belgedeki karakter sayısını <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> koleksiyonun özelliğini kullanarak belirleyebilirsiniz <xref:Microsoft.Office.Interop.Word.Characters> .

 Boşluk, paragraf işaretleri ve normalde gizlenen diğer karakterler de dahil olmak üzere belgedeki tüm karakterler sayılır. Yeni, boş bir belge de bir paragraf işareti içerdiği için bir karakter sayısını döndürür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki karakter sayısını görüntüleme

1. Belgenin tamamını seçin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. Belgedeki karakter sayısını ileti kutusunda görüntüleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>VSTO eklentideki karakter sayısını görüntüleme

1. Belgenin tamamını seçin. Aşağıdaki örnek etkin belgeyi seçer.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. Belgedeki karakter sayısını ileti kutusunda görüntüleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: aralıklarda program aracılığıyla başlangıç ve bitiş karakterlerini alma](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
