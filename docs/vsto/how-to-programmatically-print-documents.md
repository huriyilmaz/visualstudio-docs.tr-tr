---
title: 'Nasıl kullanılır: Program aracılığıyla belgeleri yazdırma'
description: Bir belgenin tamamını veya Microsoft Word bir bölümünü varsayılan yazıcınıza yazdırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a70a7b5c574e233d9597124ceb4497c4bf03742c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099769"
---
# <a name="how-to-programmatically-print-documents"></a>Nasıl kullanılır: Program aracılığıyla belgeleri yazdırma
  Word belgesinin tamamını Microsoft Office veya bir belgenin bir kısmını varsayılan yazıcınıza yazdırabilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi yazdırma

### <a name="to-print-the-entire-document"></a>Belgenin tamamını yazdırmak için

1. Belgenin <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> tamamını yazdırmak `ThisDocument` için projeniz içinde sınıfının yöntemini çağırma. Bu örneği kullanmak için sınıfından kodu `ThisDocument` çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-the-document"></a>Belgenin geçerli sayfasını yazdırmak için

1. Projeniz <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> içinde `ThisDocument` sınıfının yöntemini çağırarak geçerli sayfanın bir kopyasının yazdırılacak olduğunu belirtin. Bu örneği kullanmak için sınıfından kodu `ThisDocument` çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

## <a name="print-a-document-by-using-a-vsto-add-in"></a>VSTO Eklenti kullanarak belge yazdırma

### <a name="to-print-an-entire-document"></a>Belgenin tamamını yazdırmak için

1. Yazdırmak <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> istediğiniz <xref:Microsoft.Office.Interop.Word.Document> nesnenin yöntemini çağırma. Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından kodu çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-a-document"></a>Bir belgenin geçerli sayfasını yazdırmak için

1. Yazdırmak <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> istediğiniz nesnenin <xref:Microsoft.Office.Interop.Word.Document> yöntemini çağırarak geçerli sayfanın bir kopyasının yazdırılacak olduğunu belirtin. Aşağıdaki kod örneği etkin belgeyi yazdırır. Bu örneği kullanmak için projenizin `ThisAddIn` sınıfından kodu çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
