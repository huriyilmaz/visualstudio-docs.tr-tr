---
title: 'Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme'
description: Microsoft Word bir belgedeki metni programlı olarak biçimlendirmek için Range nesnesini nasıl kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122715"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme
  <xref:Microsoft.Office.Interop.Word.Range>bir Microsoft Office Word belgesinde metin biçimlendirmek için nesnesini kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnekte belgedeki ilk paragraf seçilir ve yazı tipi boyutu, yazı tipi adı ve hizalama değişir. Sonra aralığı seçer ve kodun sonraki bölümünü yürütmeden önce duraklatmak üzere bir ileti kutusu görüntüler. sonraki bölümde, ana bilgisayar öğesinin geri alma yöntemi <xref:Microsoft.Office.Tools.Word.Document> (belge düzeyi özelleştirmesi için) veya <xref:Microsoft.Office.Interop.Word.Document> sınıfı (VSTO eklenti için) üç kez çağrı yapılır. Normal girinti stilini uygular ve kodu duraklatmak için bir ileti kutusu görüntüler. Ardından kod <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> yöntemi bir kez çağırır ve bir ileti kutusu görüntüler.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-format-text-using-a-document-level-customization"></a>Belge düzeyi özelleştirmesi kullanarak metin biçimlendirmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesinde kullanılabilir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO eklentisi kullanarak metin biçimlendirmek için

1. aşağıdaki örnek, bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
