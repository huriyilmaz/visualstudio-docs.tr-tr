---
title: 'Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme'
description: Belgedeki metne program aracılığıyla açıklama ekleme. belge sınıfının Comments özelliği, Microsoft Word bir belgedeki metin aralığına bir açıklama ekler.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3e8b8d2f89b87d312b0a3868974fa6d9f7d039f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083355"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme
  belge sınıfının Comments özelliği, Microsoft Office Word belgesindeki bir metin aralığına bir açıklama ekler.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnek, belgedeki ilk paragrafa bir açıklama ekler.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki metne yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A>Özelliğin yöntemini çağırın <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> ve bir Aralık ve açıklama metni sağlayın. Aşağıdaki kod örneğini kullanmak için, `ThisDocument` projenizdeki sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet118":::

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>VSTO eklentideki metne yeni bir açıklama eklemek için

1. <xref:Microsoft.Office.Interop.Word.Comments.Add%2A>Özelliğin yöntemini çağırın <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> ve bir Aralık ve açıklama metni sağlayın.

     Aşağıdaki kod örneği, etkin belgeye bir açıklama ekler. Bu örneği kullanmak için, `ThisAddIn` projenizdeki sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet118":::

## <a name="robust-programming"></a>Güçlü programlama
 Word 'Ün açıklamalara eklediği Kullanıcı adının baş harflerini değiştirmek için <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> özelliğini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
