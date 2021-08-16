---
title: 'Nasıl kullanılır: Belgelerde metni program aracılığıyla gizleme'
description: Belirli bir metin aralığı için Yazı Tipi'nin Hidden özelliğini ayar Microsoft Word belgelerde metin gizlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 72e869d585f2db5163036b4e8f024d4ca4c0c620c8aec829ffcdd6ccea1cf610
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366257"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Nasıl kullanılır: Belgelerde metni program aracılığıyla gizleme
  Belirli bir metin aralığı için özelliğini <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> ayarerek belge <xref:Microsoft.Office.Interop.Word.Range.Font%2A> içinde metni gizleyebilirsiniz.

 Örneğin, yazıcıya belge göndermeden önce metni geçici olarak gizleyebilirsiniz (belge düzeyi özelleştirmede) veya <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> bir (VSTO Eklentisinde).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Belgeyi yazdırırken Yer İşareti denetiminde metni gizlemek için

1. Belirtilen aralıkta yer alan tüm metni gizleyen bir yordam oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet105":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet105":::

2. Belirtilen aralıkta yer alan tüm metinleri geri alan bir yordam oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet106":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet106":::

3. Bir yer işaretinin aralığını `HideText` yöntemine iletir, belgeyi yazdırarak aynı aralığı yöntemine `UnhideText` iletir.

     Aşağıdaki kod örneği, belge düzeyinde özelleştirmede kullanılabilir. Bu örneği kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet107":::

     Aşağıdaki kod örneği bir VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet107":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneğinde, belgenin adlı bir denetim (belge düzeyi <xref:Microsoft.Office.Tools.Word.Bookmark> özelleştirmede) veya denetim <xref:Microsoft.Office.Interop.Word.Bookmark> (bir VSTO Eklentisinde) içerdiği `bookmark1` varsaydır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl güncelleştirmesi: Yer İşareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
