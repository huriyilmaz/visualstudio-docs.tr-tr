---
title: 'Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4b2b0e2be92ca5d4b548b297d01f8ec31b779510
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519892"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma
  `DeleteAllComments`Microsoft Office Word belgesinden tüm açıklamaları kaldırmak için yöntemini kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeden tüm açıklamaları kaldırmak için

1. <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> `ThisDocument` Projenizdeki sınıfının yöntemini çağırın. Bu kod örneğini kullanmak için `ThisDocument` sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Bir belge içindeki tüm açıklamaları VSTO eklentisini kullanarak kaldırmak için

1. <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A>Açıklamalarını kaldırmak istediğiniz öğesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> .

     Aşağıdaki kod örneği, etkin belgedeki tüm açıklamaları kaldırır. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
