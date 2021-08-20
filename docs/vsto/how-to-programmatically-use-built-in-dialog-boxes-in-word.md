---
title: "Nasıl yapılır: Word'de yerleşik iletişim kutularını program aracılığıyla kullanma"
description: Visual Studio'da yerleşik iletişim kutularını program aracılığıyla kullanmak için Microsoft Word.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147992"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Nasıl yapılır: Word'de yerleşik iletişim kutularını program aracılığıyla kullanma
  Word'Microsoft Office çalışırken, kullanıcı girişi için iletişim kutularını görüntülemeye ihtiyacınız olan zamanlar vardır. Kendi iletişim kutularınızı oluşturabilirsiniz ancak Word'de nesne koleksiyonunda bulunan yerleşik iletişim kutularını kullanma <xref:Microsoft.Office.Interop.Word.Dialogs> yaklaşımını da <xref:Microsoft.Office.Interop.Word.Application> kullanabilirsiniz. Bu, numaralandırıcı olarak temsil edilen 200'den fazla yerleşik iletişim kutusuna erişmeye olanak sağlar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>İletişim kutularını görüntüleme
 Bir iletişim kutusu görüntülemek için, görüntülemek istediğiniz iletişim kutusunu temsil eden bir nesne oluşturmak için numaralama <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> değerlerinden birini kullanın. Ardından <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> nesnesinin yöntemini <xref:Microsoft.Office.Interop.Word.Dialog> çağırabilirsiniz.

 Aşağıdaki kod örneğinde Dosya Aç iletişim kutusunun **nasıl görüntüleniyor olduğu** gösterilir. Bu örneği kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Geç bağlama aracılığıyla kullanılabilen erişim iletişim kutusu üyeleri
 Word'de iletişim kutularının bazı özellikleri ve yöntemleri yalnızca geç bağlama aracılığıyla kullanılabilir. Option Strict Visual Basic nın **açık** olduğu projelerde bu üyelere erişmek için yansımayı kullanabilirsiniz. Daha fazla bilgi için [bkz. Çözümlerde Office bağlama.](../vsto/late-binding-in-office-solutions.md)

 Aşağıdaki kod örneği, **Option Strict** özelliğinin  kapalı olduğu projelerde veya ya da 'yi hedef alan Visual C# projelerinde dosya Visual Basic Dosya Aç iletişim kutusunun **Name** özelliğinin nasıl [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kullanılagelmektedir. [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Bu örneği kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Aşağıdaki kod örneği, Option Strict'nin açık olduğu  projelerde Dosya Aç iletişim kutusunun **Name** özelliğine erişmek Visual Basic **yansımanın nasıl** kullanılagelmektedir. Bu örneği kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl olur: Gizli modda Program Aracılığıyla Word iletişim kutularını kullanma](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
