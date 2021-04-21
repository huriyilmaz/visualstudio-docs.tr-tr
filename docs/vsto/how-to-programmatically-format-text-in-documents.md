---
title: 'Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme'
description: Bir Microsoft Word belgesinde programlı olarak metin biçimlendirmek için Range nesnesini nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: b91486c193b7b3fdba3b4c5cbbe86f58ffa7f06c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827883"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme
  <xref:Microsoft.Office.Interop.Word.Range>Bir Microsoft Office Word belgesinde metin biçimlendirmek için nesnesini kullanabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnekte belgedeki ilk paragraf seçilir ve yazı tipi boyutu, yazı tipi adı ve hizalama değişir. Sonra aralığı seçer ve kodun sonraki bölümünü yürütmeden önce duraklatmak üzere bir ileti kutusu görüntüler. Sonraki bölümde, ana bilgisayar öğesinin geri alma yöntemi <xref:Microsoft.Office.Tools.Word.Document> (belge düzeyi özelleştirmesi için) veya <xref:Microsoft.Office.Interop.Word.Document> Sınıf (VSTO eklentisi için) üç kez çağrı yapılır. Normal girinti stilini uygular ve kodu duraklatmak için bir ileti kutusu görüntüler. Ardından kod <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> yöntemi bir kez çağırır ve bir ileti kutusu görüntüler.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-format-text-using-a-document-level-customization"></a>Belge düzeyi özelleştirmesi kullanarak metin biçimlendirmek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesinde kullanılabilir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO eklentisini kullanarak metin biçimlendirmek için

1. Aşağıdaki örnek bir VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
