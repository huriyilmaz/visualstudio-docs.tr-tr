---
title: "Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma"
description: Microsoft Word içindeki yerleşik iletişim kutularını program aracılığıyla kullanmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 66b35e6a46ba42f64dddf54427d43bba74f10ae0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725560"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma
  Microsoft Office sözcükle çalışırken, kullanıcı girişi için iletişim kutularını görüntüetmeniz gerektiğinde zaman vardır. Kendinizinkini oluşturabilseniz de, Word 'de, nesne koleksiyonunda gösterilen yerleşik iletişim kutularını kullanma yaklaşımını de isteyebilirsiniz <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> . Bu, sabit listesi olarak temsil edilen yerleşik iletişim kutularının 200 üstünden erişmenizi sağlar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>İletişim kutularını görüntüle
 Bir iletişim kutusunu göstermek için, <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> göstermek istediğiniz iletişim kutusunu temsil eden bir nesne oluşturmak için numaralandırmanın değerlerinden birini kullanın. Ardından, <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> nesnesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Dialog> .

 Aşağıdaki kod örneği, **Dosya Aç** iletişim kutusunun nasıl görüntüleneceğini gösterir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Geç bağlama aracılığıyla kullanılabilen iletişim kutusu üyelerine erişin
 Word içindeki iletişim kutularının bazı özellikleri ve yöntemleri yalnızca geç bağlama aracılığıyla kullanılabilir. **Option Strict** açık olan Visual Basic projelerinde, bu üyelere erişmek için yansıma kullanmanız gerekir. daha fazla bilgi için bkz. [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md).

 aşağıdaki kod örneği, **Option Strict** ' in, veya ' i hedefleyen Visual C# projelerindeki Visual Basic projelerde **dosya aç** iletişim kutusunun **ad** özelliğinin nasıl kullanılacağını gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 aşağıdaki kod örneği, **seçeneğinin katı** olduğu Visual Basic projelerde **dosya aç** iletişim kutusunun **Name** özelliğine erişmek için reflection 'ın nasıl kullanılacağını gösterir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict ekstresi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
