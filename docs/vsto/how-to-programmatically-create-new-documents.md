---
title: 'Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma'
description: Visual Studio kullanarak program aracılığıyla Microsoft Word belge oluşturma hakkında Visual Studio.
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
ms.openlocfilehash: 82ca1781314585ef15fdf73e33e106108bf2c5a5e0b433eb9ae94adfa9025a2a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423910"
---
# <a name="how-to-programmatically-create-new-documents"></a>Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma
  Program aracılığıyla bir belge ekleyebilirsiniz, yeni belge yerel bir <xref:Microsoft.Office.Interop.Word.Document> nesnedir. Bu nesne, bir konak öğesinin ek olaylara ve veri bağlama <xref:Microsoft.Office.Tools.Word.Document> özelliklerine sahip değildir. Daha fazla bilgi için [bkz. Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyinde bir proje geliştirirken, projenize program aracılığıyla <xref:Microsoft.Office.Tools.Word.Document> konak öğeleri ekamazsınız. Bir VSTO projesinde, herhangi bir nesneyi çalışma <xref:Microsoft.Office.Interop.Word.Document> zamanında bir konak <xref:Microsoft.Office.Tools.Word.Document> öğeye dönüştürebilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Normal şablonunu temel alan yeni bir belge oluşturmak için

- Normal <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> şablonunu temel alan <xref:Microsoft.Office.Interop.Word.Documents> yeni bir belge oluşturmak için koleksiyonun yöntemini kullanın. Bu kod örneğini kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet1":::

## <a name="use-custom-templates"></a>Özel şablonlar kullanma
 yöntemi, <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Normal *şablonun dışında* bir şablonu temel alan yeni bir belge oluşturmak için isteğe bağlı bir Şablon bağımsız değişkenine sahip. Şablonun dosya adını ve tam yolunu sağlamak gerekir.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Özel bir şablonu temel alan yeni bir belge oluşturmak için

- Koleksiyonun <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> yöntemini <xref:Microsoft.Office.Interop.Word.Documents> çağırma ve şablonun yolunu belirtme. Bu kod örneğini kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Mevcut belgeleri program aracılığıyla açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
