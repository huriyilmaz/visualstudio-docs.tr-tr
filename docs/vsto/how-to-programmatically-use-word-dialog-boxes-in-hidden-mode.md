---
title: 'Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 923fc7ddec0350f254968fe17494ecbe27f76b13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537585"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Nasıl yapılır: gizli modda program aracılığıyla Word iletişim kutuları kullanma
  Microsoft Office Word içindeki yerleşik iletişim kutularını kullanıcıya görüntülemeden çağırarak, tek bir yöntem çağrısıyla karmaşık işlemler gerçekleştirebilirsiniz. <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> <xref:Microsoft.Office.Interop.Word.Dialog> Yöntemi çağırmak zorunda kalmadan nesne yöntemini kullanarak bunu yapabilirsiniz <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Örnekler
 Aşağıdaki kod örnekleri, Kullanıcı girişi olmadan birden çok sayfa kurulum özelliği ayarlamak için **sayfa yapısı** iletişim kutusunun gizli modda nasıl kullanılacağını göstermektedir. Örnekler <xref:Microsoft.Office.Interop.Word.Dialog> özel bir sayfa boyutunu yapılandırmak için bir nesnesi kullanır. Sayfa kurulumu için, üst kenar boşluğu, alt kenar boşluğu vb. gibi belirli ayarlar nesnenin geç bağlı özellikleri olarak kullanılabilir <xref:Microsoft.Office.Interop.Word.Dialog> . Bu özellikler, çalışma zamanında Word tarafından dinamik olarak oluşturulur.

 Aşağıdaki örnek, **Option Strict** 'in kapalı olduğu Visual Basic projelerde ve öğesini hedefleyen Visual C# projelerinde bu görevin nasıl gerçekleştirileceğini gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu projelerde Visual Basic ve Visual C# derleyicilerinin geç bağlama özelliklerini kullanabilirsiniz. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Aşağıdaki örnek, bu görevin, **seçeneğinin Strict** olduğu Visual Basic projelerinde nasıl gerçekleştirileceğini gösterir. Bu projelerde, geç bağlantılı özelliklere erişmek için yansıma kullanmanız gerekir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word 'de program aracılığıyla yerleşik iletişim kutuları kullanma](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
