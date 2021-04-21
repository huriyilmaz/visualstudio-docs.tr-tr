---
title: 'Nasıl yapılır: program aracılığıyla belgeleri kapatma'
description: Etkin belgeyi nasıl kapatabileceğinizi veya kapatılacak bir Microsoft Office Word belgesi nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1b31a35ac1fa452f526d109dd93ca8264f78947b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825361"
---
# <a name="how-to-programmatically-close-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri kapatma
  Etkin belgeyi kapatabilir veya kapatılacak bir belge belirtebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Etkin belgeyi kapat
 Etkin belgeyi kapatmak için iki yordam vardır: biri belge düzeyinde özelleştirmeler ve VSTO eklentileri için bir tane.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki etkin belgeyi kapatmak için

1. <xref:Microsoft.Office.Tools.Word.Document.Close%2A> `ThisDocument` Özelleştirmesiyle ilişkili belgeyi kapatmak için projenizdeki sınıfının yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için `ThisDocument` sınıfından çalıştırın.

    > [!NOTE]
    > Bu örnek, <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> değişiklikleri kaydetmeden veya kullanıcıya sorulmadan kapatmak için değeri *SaveChanges* parametresine geçirir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet3":::

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>VSTO eklentideki etkin belgeyi kapatmak için

1. <xref:Microsoft.Office.Interop.Word._Document.Close%2A> <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> Etkin belgeyi kapatmak için özelliği yöntemini çağırın. Aşağıdaki kod örneğini kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

    > [!NOTE]
    > Bu örnek, <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> değişiklikleri kaydetmeden veya kullanıcıya sorulmadan kapatmak için değeri *SaveChanges* parametresine geçirir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet3":::

## <a name="close-a-document-that-you-specify-by-name"></a>Ada göre belirttiğiniz bir belgeyi kapatma
 Ada göre belirttiğiniz bir belgeyi kapatmanıza olanak, VSTO eklentileri ve belge düzeyi özelleştirmeleri için aynıdır.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Ada göre belirttiğiniz bir belgeyi kapatmak için

1. Belge adını koleksiyon için bir bağımsız değişken olarak belirtin <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> ve sonra <xref:Microsoft.Office.Interop.Word._Document.Close%2A> yöntemi çağırın. Aşağıdaki kod örneği, Word 'de **NewDocument** adlı bir belgenin açık olduğunu varsayar.

    > [!NOTE]
    > Bu örnek, <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> değişiklikleri kaydetmeden veya kullanıcıya sorulmadan kapatmak için değeri *SaveChanges* parametresine geçirir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet4":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Nasıl yapılır: program aracılığıyla belgeleri kaydetme](../vsto/how-to-programmatically-save-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
