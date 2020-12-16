---
title: 'Nasıl yapılır: program aracılığıyla varolan belgeleri açma'
description: Tam nitelenmiş bir yol ve dosya adı tarafından belirtilen mevcut bir Microsoft Word belgesini açmak için Open metodunu nasıl kullanacağınızı öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525554"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Nasıl yapılır: program aracılığıyla varolan belgeleri açma
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Yöntemi, tam nitelenmiş bir yol ve dosya adı tarafından belirtilen varolan Microsoft Office Word belgesini açar. Bu yöntem <xref:Microsoft.Office.Interop.Word.Document> , açılan belgeyi temsil eden bir döndürür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Belge açmak için

- <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Koleksiyonun yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Documents> ve belge için bir yol sağlayın.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Belgeyi salt okunurdur olarak açmak için

- Yöntemi çağırın <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> , belgeye bir yol sağlayın ve yöntem çağrısında *ReadOnly* bağımsız değişkenini **true** olarak ayarlayın.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- *NewDocument.doc* adlı bir belge C sürücüsünde *Test* adlı bir dizinde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
- [Nasıl yapılır: program aracılığıyla belgeleri kapatma](../vsto/how-to-programmatically-close-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
