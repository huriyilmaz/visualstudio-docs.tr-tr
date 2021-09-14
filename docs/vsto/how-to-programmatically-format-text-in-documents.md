---
title: 'Nasıl kullanılır: Belgelerde program aracılığıyla metin biçimlendirme'
description: Bir belgeye program aracılığıyla metin biçimlendirmek için Range nesnesini nasıl Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 130469ddd084a1a044e4af458164f15c82412eef
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633937"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Nasıl kullanılır: Belgelerde program aracılığıyla metin biçimlendirme
  Word belgesinde <xref:Microsoft.Office.Interop.Word.Range> metni biçimlendirmek için nesnesini Microsoft Office kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnek, belgenin ilk paragrafı seçer ve yazı tipi boyutunu, yazı tipi adını ve hizalamayı değiştirir. Ardından aralığı seçer ve kodun sonraki bölümünü yürütmeden önce duraklatmak için bir ileti kutusu görüntüler. Sonraki bölüm, konak öğesinin Geri Al yöntemini (belge düzeyi özelleştirme için) veya <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> sınıfını (VSTO Eklenti için) üç kez çağırıyor. Normal Girinti stilini uygular ve kodu duraklatmak için bir ileti kutusu görüntüler. Ardından kod bir kez <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> yöntemini çağırarak bir ileti kutusu görüntüler.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="to-format-text-using-a-document-level-customization"></a>Belge düzeyinde özelleştirme kullanarak metin biçimlendirmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmede kullanılabilir. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti Örneği

### <a name="to-format-text-using-a-vsto-add-in"></a>Bir Eklenti kullanarak VSTO biçimlendirmek için

1. Aşağıdaki örnek, bir VSTO kullanılabilir. Bu örnek etkin belgeyi kullanır. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl kullanılır: Belgelerde program aracılığıyla metin arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
