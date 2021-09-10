---
title: İş Akışı Tasarımcısı-gecikme etkinlik Tasarımcısı
description: Gecikme etkinlikleri ve bir gecikme etkinliği oluşturmak ve yapılandırmak için gecikme etkinliği tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 71618b2ebbd0abc6f089ad9838942a99d0897e7c
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963714"
---
# <a name="delay-activity-designer"></a>Delay Etkinlik Tasarımcısı

**Gecikme** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Delay> .

## <a name="the-delay-activity"></a>Gecikme etkinliği

<xref:System.Activities.Statements.Delay>Etkinlik, bir iş akışının belirli bir süre boyunca yürütülmesini geciktirir.

### <a name="use-the-delay-activity-designer"></a>Gecikme etkinliği tasarımcısını kullanma

**Gecikme** etkinlik tasarımcısı, iş akışı Tasarımcısı araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu**' nu **temel elemanlar** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

**Gecikme** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.Delay> varsayılan gecikmeyle bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **Gecikme** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-delay-properties"></a>Gecikme özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Delay> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Delay> . Varsayılan değer gecikmede yapılır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Doğru|İş akışını geciktirmek için geçen süre. Bu özellik, özellik kılavuzunda ayarlanır. <xref:System.TimeSpan>süreyi belirtmek için 00:00:00 biçiminde veya Visual Basic ifadesinde bir sabit değer yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Ata](../workflow-designer/assign-activity-designer.md)
- [Delay Etkinlik Tasarımcısı](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)