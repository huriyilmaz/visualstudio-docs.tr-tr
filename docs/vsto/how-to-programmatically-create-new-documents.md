---
title: 'Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma'
description: Microsoft Word Visual Studio kullanarak program aracılığıyla yeni belgeler oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c52a1cffee3d87a6cd8461024c0ae7e8fab7aa08
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633950"
---
# <a name="how-to-programmatically-create-new-documents"></a>Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma
  Programlı olarak bir belge oluşturduğunuzda, yeni belge yerel bir <xref:Microsoft.Office.Interop.Word.Document> nesnedir. Bu nesne, bir konak öğesinin ek olaylarına ve veri bağlama özelliklerine sahip değil <xref:Microsoft.Office.Tools.Word.Document> . Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyi projesi geliştirirken, projenize programlama yoluyla <xref:Microsoft.Office.Tools.Word.Document> konak öğeleri ekleyemezsiniz. VSTO bir eklenti projesinde, <xref:Microsoft.Office.Interop.Word.Document> çalışma zamanında herhangi bir nesneyi bir <xref:Microsoft.Office.Tools.Word.Document> konak öğesine dönüştürebilirsiniz. daha fazla bilgi için bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Normal şablona dayalı yeni bir belge oluşturmak için

- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> <xref:Microsoft.Office.Interop.Word.Documents> Normal şablonu temel alan yeni bir belge oluşturmak için koleksiyonun yöntemini kullanın. Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet1":::

## <a name="use-custom-templates"></a>Özel Şablonlar kullanma
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>Yöntemi, normal şablondan başka bir şablonu temel alan yeni bir belge oluşturmak için isteğe bağlı bir *şablon* bağımsız değişkenine sahiptir. Şablonun dosya adını ve tam yolunu sağlamanız gerekir.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Özel bir şablonu temel alan yeni bir belge oluşturmak için

- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>Koleksiyonun yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Documents> ve şablonun yolunu belirtin. Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
