---
title: 'Nasıl yapılır: belgelerde metni program aracılığıyla gizleme'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dae19d196f830e5187fa395473c0a5482cb1d03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543318"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla gizleme
  <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> <xref:Microsoft.Office.Interop.Word.Range.Font%2A> Belirli bir metin aralığı için özelliğini ayarlayarak bir belgedeki metni gizleyebilirsiniz.

 Örneğin, bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgeyi bir yazıcıya göndermeden önce (belge düzeyi özelleştirmesinde) veya <xref:Microsoft.Office.Interop.Word.Bookmark> (VSTO eklentideki) içindeki metni geçici olarak gizleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Belgeyi yazdırırken bir yer Işareti denetimindeki metni gizlemek için

1. Belirli bir aralıktaki tüm metni gizleyen bir yordam oluşturun.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Belirli bir aralıktaki tüm metinleri gizleyen bir yordam oluşturun.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Bir yer işaretinin aralığını `HideText` yönteme geçirin, belgeyi yazdırın ve sonra aynı aralığı `UnhideText` yönteme geçirin.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir. Bu örneği kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği, belgenin <xref:Microsoft.Office.Tools.Word.Bookmark> adında bir denetim (belge düzeyi özelleştirmesi içinde) veya <xref:Microsoft.Office.Interop.Word.Bookmark> denetımı (VSTO eklentisi içinde) içerdiğini varsayar `bookmark1` .

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: yer Işareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
