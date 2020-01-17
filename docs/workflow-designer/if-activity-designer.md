---
title: İş Akışı Tasarımcısı-If etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111467"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı

<xref:System.Activities.Statements.If> etkinliği bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, programlama için bir yordamsal modelleme stili kullanırken faydalıdır. Bir <xref:System.Activities.Statements.If> etkinlik, örneğin bir <xref:System.Activities.Statements.Sequence> etkinliğinin veya <xref:System.Activities.Statements.Parallel> etkinliğinin içinde iç içe olabilir. <xref:System.Activities.Statements.Flowchart> etkinlik kullanıyorsanız bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinlik kullanmayı düşünün.

## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.If> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Hangi alt etkinliğin çalıştırılacağını belirleyen koşul. <xref:System.Activities.Statements.If.Condition%2A>ayarlamak için, **IF** Etkinlik tasarımcısında veya özellik kılavuzunda **koşul** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.If.Else%2A>|False|<xref:System.Activities.Statements.If.Condition%2A> **false**ise yürütülecek etkinlik. <xref:System.Activities.Statements.If.Else%2A> Dalı tarafından yürütülen bir etkinlik eklemek için, **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" ipucu metni ile **IF** Etkinlik tasarımcısında **Else** kutusuna bırakın.|
|<xref:System.Activities.Statements.If.Then%2A>|False|<xref:System.Activities.Statements.If.Condition%2A> **true**ise yürütülecek etkinlik. <xref:System.Activities.Statements.If.Then%2A> Dalı tarafından yürütülen bir etkinlik eklemek için, **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" ipucu metni ile **IF** Etkinlik tasarımcısında **bulunan kutuya bırakın** .|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
