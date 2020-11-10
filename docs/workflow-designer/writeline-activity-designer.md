---
title: İş Akışı Tasarımcısı-WriteLine etkinlik Tasarımcısı
description: WriteLine etkinliği ve bir WriteLine etkinliği oluşturmak ve yapılandırmak için WriteLine etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 03aedaf522924266b0951ec189e96fb3f83c142c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433667"
---
# <a name="writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısı

**WriteLine** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.WriteLine> .

## <a name="the-writeline-activity"></a>WriteLine etkinliği

<xref:System.Activities.Statements.WriteLine>Etkinlik, belirtilen bir nesneye metin yazar <xref:System.IO.TextWriter> . Hayır <xref:System.IO.TextWriter> belirtilmişse, <xref:System.Activities.Statements.WriteLine> metni konsola yazar.

### <a name="using-the-writeline-activity-designer"></a>WriteLine etkinlik tasarımcısını kullanma

**Araç kutusunun** **temel elemanlar** kategorisindeki **WriteLine** etkinlik tasarımcısına erişin. **WriteLine** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.WriteLine> , varsayılan olarak WriteLine olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **WriteLine** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-writeline-properties"></a>WriteLine özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.WriteLine> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.WriteLine> . Varsayılan değer WriteLine ' dır. <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Yanlış|Yazılacak metin. Özelliği ayarlamak için, **WriteLine** etkinlik Tasarımcısı ' nın veya özellik kılavuzundaki **metin** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Yanlış|' A <xref:System.IO.TextWriter> <xref:System.Activities.Statements.WriteLine> Yazar <xref:System.Activities.Statements.WriteLine.Text%2A> . Varsayılan, konsoldur.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Ata](../workflow-designer/assign-activity-designer.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
