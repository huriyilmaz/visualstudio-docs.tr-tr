---
title: If etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659066"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı
@No__t_0 etkinliği bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, programlama için bir yordamsal modelleme stili kullanırken faydalıdır. Bir <xref:System.Activities.Statements.If> etkinlik, örneğin bir <xref:System.Activities.Statements.Sequence> etkinliğinin veya <xref:System.Activities.Statements.Parallel> etkinliğinin içinde iç içe olabilir. @No__t_0 etkinlik kullanıyorsanız bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinlik kullanmayı düşünün.

## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.If> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Hangi alt etkinliğin çalıştırılacağını belirleyen koşul. @No__t_0 ayarlamak için, **IF** Etkinlik tasarımcısında veya özellik kılavuzunda **koşul** kutusuna bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesi yazın.|
|<xref:System.Activities.Statements.If.Else%2A>|False|@No__t_0 **false**ise yürütülecek etkinlik. @No__t_0 Dalı tarafından yürütülen bir etkinlik eklemek için, **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" ipucu metni ile **IF** Etkinlik tasarımcısında **Else** kutusuna bırakın.|
|<xref:System.Activities.Statements.If.Then%2A>|False|@No__t_0 **true**ise yürütülecek etkinlik. @No__t_0 Dalı tarafından yürütülen bir etkinlik eklemek için, **araç kutusundan** bir etkinliği, ipucu metin olarak "etkinliği buraya bırak" ipucu metni ile **IF** Etkinlik tasarımcısında **bulunan kutuya bırakın** .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Sıralı](../workflow-designer/sequence-activity-designer.md) [paralel](../workflow-designer/parallel-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)