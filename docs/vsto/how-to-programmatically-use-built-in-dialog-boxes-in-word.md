---
title: "Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma"
description: Visual Studio 'Yu kullanarak Microsoft Word 'de yerleşik iletişim kutularını programlı bir şekilde nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b2c1a748d38c2b649705fa1ad2de21553b710634
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523618"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma
  Microsoft Office sözcükle çalışırken, Kullanıcı girişi için iletişim kutularını görüntüetmeniz gerektiğinde zaman vardır. Kendinizinkini oluşturabilseniz de, Word 'de, nesne koleksiyonunda gösterilen yerleşik iletişim kutularını kullanma yaklaşımını de isteyebilirsiniz <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> . Bu, sabit listesi olarak temsil edilen yerleşik iletişim kutularının 200 üstünden erişmenizi sağlar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>İletişim kutularını görüntüle
 Bir iletişim kutusunu göstermek için, <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> göstermek istediğiniz iletişim kutusunu temsil eden bir nesne oluşturmak için numaralandırmanın değerlerinden birini kullanın. Ardından, <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> nesnesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Dialog> .

 Aşağıdaki kod örneği, **Dosya Aç** iletişim kutusunun nasıl görüntüleneceğini gösterir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Geç bağlama aracılığıyla kullanılabilen iletişim kutusu üyelerine erişin
 Word içindeki iletişim kutularının bazı özellikleri ve yöntemleri yalnızca geç bağlama aracılığıyla kullanılabilir. **Option Strict** açık olan Visual Basic projelerinde, bu üyelere erişmek için yansıma kullanmanız gerekir. Daha fazla bilgi için bkz. [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).

 Aşağıdaki kod örneği, **Option Strict** ' in, veya ' i hedefleyen Visual C# projelerindeki Visual Basic projelerde **Dosya Aç** iletişim kutusunun **ad** özelliğinin nasıl kullanılacağını gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Aşağıdaki kod örneği, **seçeneğinin katı** olduğu Visual Basic projelerde **Dosya Aç** iletişim kutusunun **Name** özelliğine erişmek için Reflection 'ın nasıl kullanılacağını gösterir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict ekstresi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
