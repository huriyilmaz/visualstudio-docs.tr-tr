---
title: İş Akışı Tasarımcısı-WriteLine etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593030"
---
# <a name="writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısı

**WriteLine** etkinlik Tasarımcısı <xref:System.Activities.Statements.WriteLine> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-writeline-activity"></a>WriteLine etkinliği

<xref:System.Activities.Statements.WriteLine> etkinliği, belirtilen bir <xref:System.IO.TextWriter> nesnesine metin yazar. <xref:System.IO.TextWriter> belirtilmemişse, <xref:System.Activities.Statements.WriteLine> metni konsola yazar.

### <a name="using-the-writeline-activity-designer"></a>WriteLine etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **WriteLine** etkinlik tasarımcısına erişin. **WriteLine** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence>içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, WriteLine 'ın varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **WriteLine** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-writeline-properties"></a>WriteLine özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.WriteLine> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> etkinliğinin kolay adı. Varsayılan değer WriteLine ' dır. <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Yazılacak metin. Özelliği ayarlamak için, **WriteLine** etkinlik Tasarımcısı ' nın veya özellik kılavuzundaki **metin** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A>yazdığı <xref:System.IO.TextWriter>. Varsayılan, konsoldur.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
