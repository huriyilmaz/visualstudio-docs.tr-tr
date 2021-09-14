---
title: 'Nasıl yapılır: program aracılığıyla varolan belgeleri açma'
description: tam nitelenmiş bir yol ve dosya adı tarafından belirtilen mevcut bir Microsoft Word belgeyi açmak için open metodunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e1785053c4342144e56cb67e1f75adbef484058b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725566"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Nasıl yapılır: program aracılığıyla varolan belgeleri açma
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>yöntemi, tam nitelenmiş bir yol ve dosya adı tarafından belirtilen varolan Microsoft Office Word belgesini açar. Bu yöntem <xref:Microsoft.Office.Interop.Word.Document> , açılan belgeyi temsil eden bir döndürür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Belge açmak için

- <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Koleksiyonun yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Documents> ve belge için bir yol sağlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet5":::

## <a name="to-open-a-document-as-read-only"></a>Belgeyi salt okunurdur olarak açmak için

- Yöntemi çağırın <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> , belgeye bir yol sağlayın ve yöntem çağrısında *ReadOnly* bağımsız değişkenini **true** olarak ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet6":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- *NewDocument.doc* adlı bir belge C sürücüsünde *Test* adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
- [Nasıl yapılır: program aracılığıyla belgeleri kapatma](../vsto/how-to-programmatically-close-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
