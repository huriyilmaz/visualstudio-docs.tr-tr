---
title: 'Nasıl kullanılır: Belgelere program aracılığıyla üst bilgiler ve alt bilgiler ekleme'
description: Bölümü'nin Headers özelliğini ve Footers özelliğini kullanarak belgenizin üst bilgilerine ve alt bilgilerine metin ekleme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b2ddbc24bcd567ce56326a4b96d9c97f1e50061c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106295"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Nasıl kullanılır: Belgelere program aracılığıyla üst bilgiler ve alt bilgiler ekleme
  özelliğini ve özelliğini kullanarak belgenizin üst bilgilerine ve alt <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> bilgilerine <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> metin <xref:Microsoft.Office.Interop.Word.Section> ekleyebilirsiniz. Belgenin her bölümü üç üst bilgi ve alt bilgi içerir:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Yordamlar, belge düzeyi özelleştirmeler ve VSTO için farklıdır.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 Aşağıdaki kod örneklerini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

### <a name="to-add-text-to-footers-in-the-document"></a>Belgede alt bilgilere metin eklemek için

1. Aşağıdaki kod örneği belgenin her bölümünün birincil alt bilgisine eklenecek metnin yazı tipini ayarlar ve ardından alt bilgiye metin ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Belgede üst bilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgenin her üst bilgisinde sayfa numarasını göstermek için bir alan ekler ve sonra metnin üst bilginin sağ tarafından hizalanması için paragraf hizalamasını ayarlar.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>VSTO Eklentiler
 Aşağıdaki kod örneklerini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

### <a name="to-add-text-to-footers-in-a-document"></a>Belgede alt bilgilere metin eklemek için

1. Aşağıdaki kod örneği belgenin her bölümünün birincil alt bilgisine eklenecek metnin yazı tipini ayarlar ve ardından alt bilgiye metin ekler. Bu kod örneği etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Belgede üst bilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgenin her üst bilgisinde sayfa numarasını göstermek için bir alan ekler ve sonra metnin üst bilginin sağ tarafından hizalanması için paragraf hizalamasını ayarlar. Bu kod örneği etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
