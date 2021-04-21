---
title: 'Nasıl yapılır: belgelerde metni program aracılığıyla gizleme'
description: Belirli bir metin aralığı için yazı tipinin gizli özelliğini ayarlayarak bir Microsoft Word belgesindeki metni nasıl gizleyebileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 04ea6b56519656782a3e408892235fa177eef755
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826492"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla gizleme
  <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> <xref:Microsoft.Office.Interop.Word.Range.Font%2A> Belirli bir metin aralığı için özelliğini ayarlayarak bir belgedeki metni gizleyebilirsiniz.

 Örneğin, bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgeyi bir yazıcıya göndermeden önce (belge düzeyi özelleştirmesinde) veya <xref:Microsoft.Office.Interop.Word.Bookmark> (VSTO eklentideki) içindeki metni geçici olarak gizleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Belgeyi yazdırırken bir yer Işareti denetimindeki metni gizlemek için

1. Belirli bir aralıktaki tüm metni gizleyen bir yordam oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet105":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet105":::

2. Belirli bir aralıktaki tüm metinleri gizleyen bir yordam oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet106":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet106":::

3. Bir yer işaretinin aralığını `HideText` yönteme geçirin, belgeyi yazdırın ve sonra aynı aralığı `UnhideText` yönteme geçirin.

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir. Bu örneği kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet107":::

     Aşağıdaki kod örneği bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Örneği kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet107":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği, belgenin <xref:Microsoft.Office.Tools.Word.Bookmark> adında bir denetim (belge düzeyi özelleştirmesi içinde) veya <xref:Microsoft.Office.Interop.Word.Bookmark> denetımı (VSTO eklentisi içinde) içerdiğini varsayar `bookmark1` .

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: yer Işareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
