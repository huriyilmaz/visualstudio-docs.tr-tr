---
title: 'Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 04d4ffdc747823a3df9a884b054b39ad484e09a4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583794"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme
  Belge sınıfının Comments Özelliği, Microsoft Office Word belgesindeki bir metin aralığına bir açıklama ekler.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnek, belgedeki ilk paragrafa bir açıklama ekler.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki metne yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A>Özelliğin yöntemini çağırın <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> ve bir Aralık ve açıklama metni sağlayın. Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>VSTO eklentideki metne yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A>Özelliğin yöntemini çağırın <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> ve bir Aralık ve açıklama metni sağlayın.

     Aşağıdaki kod örneği, etkin belgeye bir açıklama ekler. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Güçlü programlama
 Word 'Ün açıklamalara eklediği Kullanıcı adının baş harflerini değiştirmek için <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> özelliğini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
