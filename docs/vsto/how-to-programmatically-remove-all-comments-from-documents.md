---
title: 'Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma'
description: Visual Studio 'Yu kullanarak bir Microsoft Word belgesinden tüm açıklamaları programlı bir şekilde nasıl kaldırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d51f44537c4e9564162d458c564dd428e57d154
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827051"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Nasıl yapılır: belgelerden tüm açıklamaları program aracılığıyla kaldırma
  `DeleteAllComments`Microsoft Office Word belgesinden tüm açıklamaları kaldırmak için yöntemini kullanın.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeden tüm açıklamaları kaldırmak için

1. <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> `ThisDocument` Projenizdeki sınıfının yöntemini çağırın. Bu kod örneğini kullanmak için `ThisDocument` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet119":::

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Bir belge içindeki tüm açıklamaları VSTO eklentisini kullanarak kaldırmak için

1. <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A>Açıklamalarını kaldırmak istediğiniz öğesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> .

     Aşağıdaki kod örneği, etkin belgedeki tüm açıklamaları kaldırır. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet119":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metne program aracılığıyla açıklama ekleme](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
