---
title: İş Akışı Tasarımcısı-akış çizelgesi etkinlik Tasarımcısı
description: Karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için akış çizelgesi etkinliğini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: e6b00356debe67e87410a1be9112af59c305906096d96a34417802b1fd917dcf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408064"
---
# <a name="flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Flowchart>Etkinlik, karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için kullanılır. Bir <xref:System.Activities.Statements.Flowchart> kod içinde ya da iş akışı Tasarımcısı kullanılarak yazılabilir. Bu konu, İş Akışı Tasarımcısı deneyimini belgelemektedir. İş Akışı Tasarımcısı iş akışı etkinliği Tasarımcısı, geliştiricilerin iş akışlarını doğal bir şekilde yazarmasını sağlar.

## <a name="the-flowchart-activity"></a>Akış çizelgesi etkinliği

, <xref:System.Activities.Statements.Flowchart> <xref:System.Activities.Statements.Flowchart.StartNode%2A> İş akışı başladığında yürütülen bir benzersiz belirtir ve <xref:System.Activities.Statements.Flowchart.Nodes%2A> rastgele döngüler oluşturmak veya herhangi bir zamanda iş akışındaki herhangi bir yere yürütme akışını yapmak için bağlantılı bir ağı kullanır.

### <a name="using-the-flowchart-activity-designer"></a>Akış çizelgesi etkinlik tasarımcısını kullanma

**Akış çizelgesi** etkinlik **Tasarımcısı, iş akışı Tasarımcısı araç çubuğu kategorisinde bulunabilir** **ve bu,** **araç kutusu** sekmesine tıklanarak erişilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

**Akış çizelgesi** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, etkinlik tasarımcılarının bir kök etkinlik olarak veya başka bir denetim akışı etkinliğinin alt öğesi olarak yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. **Akış çizelgesi** etkinlik Tasarımcısı boş bir iş akışı Tasarımcısı yüzeyi üzerine bırakıldığında, <xref:System.Activities.Statements.Flowchart> Varsayılan olarak kendisini yürütmeyi Başlatan başlangıç düğümünün yeşil bir top olarak temsil edildiği genişletilmiş bir görünümde gösterir. **Akış çizelgesi** etkinlik Tasarımcısı başka bir denetim akışı etkinliğine bırakıldığında, kendisini, **akış çizelgesi** etkinlik tasarımcısına çift tıklayarak genişletilebilen, simge durumuna küçültülmüş bir görünümde sunar. **Araç kutusundaki** herhangi bir etkinlik, diğer denetim akışı etkinlikleri dahil olmak üzere doğrudan **akış çizelgesi** etkinlik tasarımcısına sürüklenebilir.

Çeşitli etkinlik tasarımcılarını İş Akışı Tasarımcısı tuvaline sürükledikten sonra <xref:System.Activities.Activity> temsil ettikleri nesneler, yürütme sırasını belirtmek için birbirine bağlanabilir. Kaynak etkinlik ve hedef etkinlik arasında bir bağlantı oluşturmak için, kaynak etkinliği ve kare tutamaçları tasarlayıcı üzerinde fare, onun her tarafında görünür. Kare tutamaçlardan birine tıklayın ve fare düğmesini fareyle üzerine gelindiğinde hedef etkinliğin etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki etkinlik arasında bir bağlantı oluşturulur.

### <a name="flowchart-activity-properties"></a>Akış çizelgesi etkinlik özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Flowchart> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının görünen adını belirtir. Varsayılan değer akış çizelgesi ' dir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Yanlış|Bunun içinde kapsamı belirlenmiş değişkenlerin koleksiyonu, <xref:System.Activities.Statements.Flowchart> alt etkinlikleri genelinde durum paylaşmalıdır.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Yanlış|<xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.Flowchart> Başlatıldığında yürütülür.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Yanlış|İçindeki nesnelerin koleksiyonunu içerir <xref:System.Activities.Statements.FlowNode> <xref:System.Activities.Statements.Flowchart> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
