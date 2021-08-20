---
title: İş Akışı Tasarımcısı - If Etkinlik Tasarımcısı
description: If etkinliğinin bir koşulu nasıl değerlendirip bu değerlendirmenin sonuçlarına bağlı olarak bir etkinlik yürütmesini öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155167"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı

Etkinlik <xref:System.Activities.Statements.If> bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik en çok programlamanın yordamsal modelleme stilini kullanırken kullanışlıdır. Bir <xref:System.Activities.Statements.If> etkinlik, örneğin bir etkinliğin <xref:System.Activities.Statements.Sequence> veya <xref:System.Activities.Statements.Parallel> etkinliğin içinde iç içe yer alan bir etkinlik olabilir. Bir etkinlik kullanıyorsanız <xref:System.Activities.Statements.Flowchart> bunun yerine bir etkinlik kullanmayı göz önünde <xref:System.Activities.Statements.FlowDecision> bulundurarak.

## <a name="if-properties-in-the-workflow-designer"></a>If Properties in the İş Akışı Tasarımcısı

Aşağıdaki tabloda en kullanışlı etkinlik <xref:System.Activities.Statements.If> özellikleri ve bunların tasarımcıda nasıl kullanacağız açık bulunmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Hangi alt etkinliğin yürütülecek olduğunu belirleyen koşul. ayarlamak için, If Visual Basic tasarımcısında veya özellik kılavuzunda Koşul kutusuna bir Visual Basic <xref:System.Activities.Statements.If.Condition%2A> ifadesi yazın.  |
|<xref:System.Activities.Statements.If.Else%2A>|Yanlış|false ise <xref:System.Activities.Statements.If.Condition%2A> yürütülecek **etkinlik.** Dal tarafından yürütülen bir etkinliği eklemek için Araç Kutusundan If etkinlik tasarımcısının Else kutusuna "Etkinliği Buraya Bırak" ipucu metniyle bir <xref:System.Activities.Statements.If.Else%2A> etkinlik bırakın.   |
|<xref:System.Activities.Statements.If.Then%2A>|Yanlış|true ise <xref:System.Activities.Statements.If.Condition%2A> yürütülecek **etkinlik.** Dal tarafından yürütülen bir etkinliği eklemek için Araç Kutusundan If etkinlik tasarımcısının Ardından kutusuna "Etkinliği Buraya Bırak" ipucu metniyle bir <xref:System.Activities.Statements.If.Then%2A> etkinlik bırakın.   |

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Paralel](../workflow-designer/parallel-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
