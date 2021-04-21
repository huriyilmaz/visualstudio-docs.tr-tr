---
title: 'Nasıl yapılır: belgelere program aracılığıyla üstbilgiler ve altbilgiler ekleme'
description: Bölümünün üstbilgiler özelliği ve altbilgileri özelliğini kullanarak belgenizdeki üstbilgilere ve altbilgilere nasıl metin ekleyebileceğiniz hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828754"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Nasıl yapılır: belgelere program aracılığıyla üstbilgiler ve altbilgiler ekleme
  Özelliği ve özelliğini kullanarak belgenizdeki üstbilgilere ve altbilgilere metin ekleyebilirsiniz <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> <xref:Microsoft.Office.Interop.Word.Section> . Bir belgenin her bölümü üç üst bilgi ve alt bilgi içerir:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Yordamlar belge düzeyinde özelleştirmeler ve VSTO eklentileri için farklıdır.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler
 Aşağıdaki kod örneklerini kullanmak için, bunları `ThisDocument` projenizdeki sınıfından çalıştırın.

### <a name="to-add-text-to-footers-in-the-document"></a>Belgedeki altbilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgenin her bölümünün birincil altbilgisine eklenecek metnin yazı tipini ayarlar ve altbilgiye metin ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Belgedeki üstbilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgedeki her bir başlıktaki sayfa numarasını göstermek için bir alan ekler ve sonra metnin üstbilginin sağına hizalanmasını sağlayacak şekilde paragraf hizalamasını ayarlar.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>VSTO eklentileri
 Aşağıdaki kod örneklerini kullanmak için, bunları `ThisAddIn` projenizdeki sınıfından çalıştırın.

### <a name="to-add-text-to-footers-in-a-document"></a>Belgedeki altbilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgenin her bölümünün birincil altbilgisine eklenecek metnin yazı tipini ayarlar ve altbilgiye metin ekler. Bu kod örneği etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Belgedeki üstbilgilere metin eklemek için

1. Aşağıdaki kod örneği, belgedeki her bir başlıktaki sayfa numarasını göstermek için bir alan ekler ve sonra metnin üstbilginin sağına hizalanmasını sağlayacak şekilde paragraf hizalamasını ayarlar. Bu kod örneği etkin belgeyi kullanır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
