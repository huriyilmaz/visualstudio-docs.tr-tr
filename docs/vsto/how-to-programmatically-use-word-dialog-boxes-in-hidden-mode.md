---
title: 'Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma'
description: gizli modda Microsoft Word iletişim kutularını program aracılığıyla kullanmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ca6d7f1e14904497ecb756936b996b64311a8423
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083043"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma
  Microsoft Office Word içindeki yerleşik iletişim kutularını kullanıcıya görüntülemeden çağırarak, tek bir yöntem çağrısıyla karmaşık işlemler gerçekleştirebilirsiniz. <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> <xref:Microsoft.Office.Interop.Word.Dialog> Yöntemi çağırmak zorunda kalmadan nesne yöntemini kullanarak bunu yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Örnekler
 Aşağıdaki kod örnekleri, Kullanıcı girişi olmadan birden çok sayfa kurulum özelliği ayarlamak için **sayfa yapısı** iletişim kutusunun gizli modda nasıl kullanılacağını göstermektedir. Örnekler <xref:Microsoft.Office.Interop.Word.Dialog> özel bir sayfa boyutunu yapılandırmak için bir nesnesi kullanır. Sayfa kurulumu için, üst kenar boşluğu, alt kenar boşluğu vb. gibi belirli ayarlar nesnenin geç bağlı özellikleri olarak kullanılabilir <xref:Microsoft.Office.Interop.Word.Dialog> . Bu özellikler, çalışma zamanında Word tarafından dinamik olarak oluşturulur.

 aşağıdaki örnek, **Option Strict** 'in kapalı olduğu Visual Basic projelerde ve öğesini hedefleyen Visual C# projelerinde bu görevin nasıl gerçekleştirileceğini gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . bu projelerde Visual Basic ve Visual C# derleyicilerinin geç bağlama özelliklerini kullanabilirsiniz. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 aşağıdaki örnek, bu görevin, **seçeneğinin Strict** olduğu Visual Basic projelerinde nasıl gerçekleştirileceğini gösterir. Bu projelerde, geç bağlantılı özelliklere erişmek için yansıma kullanmanız gerekir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
