---
title: İş Akışı Tasarımcısı-etkinlik Tasarımcısı atama
description: Atama etkinliği oluşturma ve yapılandırma ve atama etkinliğinin bir değişkene veya bağımsız değişkene değer atama şeklini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b10e12302b2fd11a2e4aec9266e5ad517a1edb4ad47e8b64dde44df79847825e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408077"
---
# <a name="assign-activity-designer"></a>Assign Etkinlik Tasarımcısı

Etkinlik oluşturma ve yapılandırma etkinliği için **atama** etkinliği Tasarımcısı kullanılır <xref:System.Activities.Statements.Assign> .

## <a name="the-assign-activity"></a>Atama etkinliği

<xref:System.Activities.Statements.Assign>Etkinlik bir değişkene veya bağımsız değişkene bir değer atar.

### <a name="using-the-assign-activity-designer"></a>Atama etkinliği tasarımcısını kullanma

**Ata** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak **erişilen araç kutusu**' nda (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek) bulunan **temel öğeler** kategorisinde bulunabilir.

**Atama** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, içinde olduğu gibi, herhangi bir etkinliğin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . **Atama** etkinliği Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.Assign> varsayılan ata **DisplayName** ile bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Atama** etkinliğinin üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-assign-properties"></a>Atama özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Assign> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Assign> . Varsayılan değer atama ' dır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Assign.To%2A>|Doğru|Atandığı değişken veya bağımsız değişken <xref:System.Activities.Statements.Assign.Value%2A> . değer geçerli bir Visual Basic tanımlayıcısı olmalıdır. özelliği ayarlamak için, **Assign** activity designer 'daki **To** kutusuna veya özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Doğru|Değişkene atanan değer. <xref:System.Activities.Statements.Assign.Value%2A>' ı ayarlamak için, bir Visual Basic ifadesi ' ni **ata** veya özellik kılavuzunda **değer** kutusuna yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Gecikme](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)