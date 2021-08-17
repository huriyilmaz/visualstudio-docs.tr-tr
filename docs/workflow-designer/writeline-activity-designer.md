---
title: İş Akışı Tasarımcısı - WriteLine Etkinlik Tasarımcısı
description: WriteLine etkinliği ve WriteLine etkinlik tasarımcısını kullanarak WriteLine etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: daa88d858af5b99beda41631c6c139be9aff425d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025179"
---
# <a name="writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısı

Etkinlik oluşturmak ve yapılandırmak için **WriteLine** etkinlik tasarımcısı <xref:System.Activities.Statements.WriteLine> kullanılır.

## <a name="the-writeline-activity"></a>WriteLine Etkinliği

Etkinlik, <xref:System.Activities.Statements.WriteLine> belirtilen bir nesneye metin <xref:System.IO.TextWriter> yazar. <xref:System.IO.TextWriter>Belirtilmezse, <xref:System.Activities.Statements.WriteLine> metni konsola yazar.

### <a name="using-the-writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Temel Öğeler **kategorisindeki** **WriteLine** etkinlik **tasarımcısına erişin.** **WriteLine etkinlik** tasarımcısı, **Araç** Kutusundan sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirilmelerinden sonra araç yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.WriteLine> WriteLine değerine <xref:System.Activities.Activity.DisplayName%2A> sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **WriteLine** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-writeline-properties"></a>WriteLine Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.WriteLine> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazı özellikler yüzeyde İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.WriteLine> adı. Varsayılan değer WriteLine'dır. kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Yanlış|Yazacak metin. Özelliğini ayarlamak için, **WriteLine** Visual Basic tasarımcısının **Metin** kutusuna veya özellik kılavuzuna bir metin ifadesi yazın.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Yanlış|, <xref:System.IO.TextWriter> <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> yazar. Varsayılan olarak konsol kullanılır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Atamak](../workflow-designer/assign-activity-designer.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
