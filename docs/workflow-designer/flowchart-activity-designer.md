---
title: İş Akışı Tasarımcısı-akış çizelgesi etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f56c7eac56572d8a3be1f8b478feb0543390481
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650450"
---
# <a name="flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı

@No__t_0 etkinliği, karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için kullanılır. @No__t_0 kodda ya da İş Akışı Tasarımcısı kullanılarak yazılabilir. Bu konu, İş Akışı Tasarımcısı deneyimini belgelemektedir. İş Akışı Tasarımcısı iş akışı etkinliği Tasarımcısı, geliştiricilerin iş akışlarını doğal bir şekilde yazarmasını sağlar.

## <a name="the-flowchart-activity"></a>Akış çizelgesi etkinliği

@No__t_0, iş akışı başlatıldığında yürütülen benzersiz bir <xref:System.Activities.Statements.Flowchart.StartNode%2A> belirtir ve rastgele döngüler oluşturmak veya herhangi bir zamanda iş akışındaki herhangi bir yere yürütme akışını yapmak için bağlantılı <xref:System.Activities.Statements.Flowchart.Nodes%2A> ağını kullanır.

### <a name="using-the-flowchart-activity-designer"></a>Akış çizelgesi etkinlik tasarımcısını kullanma

**Akış çizelgesi** etkinlik **Tasarımcısı, iş akışı Tasarımcısı araç çubuğu kategorisinde bulunabilir** **ve bu,** **araç kutusu** sekmesine tıklanarak erişilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

**Akış çizelgesi** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, etkinlik tasarımcılarının bir kök etkinlik olarak veya başka bir denetim akışı etkinliğinin alt öğesi olarak yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. **Akış çizelgesi** etkinlik Tasarımcısı boş bir iş akışı Tasarımcısı yüzeyi üzerine bırakıldığında, varsayılan olarak kendisini yürütmeyi Başlatan başlangıç düğümünün yeşil bir top olarak temsil edildiği genişletilmiş bir görünümde sunan bir <xref:System.Activities.Statements.Flowchart> etkinliği oluşturur. **Akış çizelgesi** etkinlik Tasarımcısı başka bir denetim akışı etkinliğine bırakıldığında, kendisini, **akış çizelgesi** etkinlik tasarımcısına çift tıklayarak genişletilebilen, simge durumuna küçültülmüş bir görünümde sunar. **Araç kutusundaki** herhangi bir etkinlik, diğer denetim akışı etkinlikleri dahil olmak üzere doğrudan **akış çizelgesi** etkinlik tasarımcısına sürüklenebilir.

Çeşitli etkinlik tasarımcılarını İş Akışı Tasarımcısı tuvaline sürükledikten sonra, temsil ettikleri <xref:System.Activities.Activity> nesneleri, yürütme sırasını belirtmek için birbirine bağlanabilir. Kaynak etkinlik ve hedef etkinlik arasında bir bağlantı oluşturmak için, kaynak etkinliği ve kare tutamaçları tasarlayıcı üzerinde fare, onun her tarafında görünür. Kare tutamaçlardan birine tıklayın ve fare düğmesini fareyle üzerine gelindiğinde hedef etkinliğin etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki etkinlik arasında bir bağlantı oluşturulur.

### <a name="flowchart-activity-properties"></a>Akış çizelgesi etkinlik özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Flowchart> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Başlıktaki etkinlik tasarımcısının görünen adını belirtir. Varsayılan değer akış çizelgesi ' dir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Bu <xref:System.Activities.Statements.Flowchart> kapsamındaki değişkenlerin koleksiyonu, alt etkinlikleri genelinde durum paylaşmalıdır.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|@No__t_1 başladığında yürütülen <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|@No__t_1 <xref:System.Activities.Statements.FlowNode> nesnelerinin koleksiyonunu içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)