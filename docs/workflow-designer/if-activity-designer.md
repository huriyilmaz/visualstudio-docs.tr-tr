---
title: İş Akışı Tasarımcısı-If etkinlik Tasarımcısı
description: Etkinliğin bir koşulu nasıl değerlendirdiğine ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği nasıl yürüttüğünü öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 6abacbe5f5212a062c9f23cdc7cfab3e27d7cb6b
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963753"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı

<xref:System.Activities.Statements.If>Etkinlik bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, programlama için bir yordamsal modelleme stili kullanırken faydalıdır. <xref:System.Activities.Statements.If>Etkinlik, örneğin bir etkinliğin veya etkinliğin içinde iç içe olabilir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Parallel> . Bir <xref:System.Activities.Statements.Flowchart> etkinlik kullanıyorsanız <xref:System.Activities.Statements.FlowDecision> bunun yerine bir etkinlik kullanmayı düşünün.

## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.If> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Hangi alt etkinliğin çalıştırılacağını belirleyen koşul. ayarlamak için, <xref:System.Activities.Statements.If.Condition%2A> **ıf** etkinlik tasarımcısında veya özellik kılavuzunda **koşul** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.If.Else%2A>|Yanlış|False ise yürütülecek etkinlik <xref:System.Activities.Statements.If.Condition%2A> .  Dal tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Else%2A> , **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" Ipucu metni ile **IF** Etkinlik tasarımcısında **Else** kutusuna bırakın.|
|<xref:System.Activities.Statements.If.Then%2A>|Yanlış|True ise yürütülecek etkinlik <xref:System.Activities.Statements.If.Condition%2A> .  Dal tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Then%2A> , **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya  bırak" ipucu metni ile **IF** Etkinlik tasarımcısında bulunan kutuya bırakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Dir](../workflow-designer/parallel-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
