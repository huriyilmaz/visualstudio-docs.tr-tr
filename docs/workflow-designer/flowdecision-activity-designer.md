---
title: İş Akışı Tasarımcısı-Flowkarar etkinlik Tasarımcısı
description: Flowkarar düğümünün, denetimin akışı için iki alternatifden birine bir dal sağlayan bir koşullu düğüm olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 82e51de857855f6b65fd71d0a070ef8d4a49e5aaca8f5eee1c47a33e72ef5781
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243477"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı

<xref:System.Activities.Statements.FlowDecision>Düğüm, belirtilen koşulun karşılanmasına bağlı olarak, denetimin iki alternatifden birine akışı için bir dal sağlayan koşullu bir düğümdür. Akışta ikiden fazla dal gerekiyorsa, <xref:System.Activities.Statements.FlowSwitch%601> bunun yerine kullanın.

## <a name="the-flowdecision-node"></a>Flowkarar düğümü

<xref:System.Activities.Statements.FlowDecision>Akışın iki yola dallandırılmasına yol açabilir. Bir <xref:System.Activities.Statements.FlowDecision> düğüm, <xref:System.Activities.Statements.FlowDecision.Condition%2A> ve <xref:System.Activities.Statements.FlowNode> her iki olası sonuç ile ilişkili bir ve içerir: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A> . <xref:System.Activities.Statements.FlowDecision.Condition%2A>Değerlendirilir ve bu değerlendirmenin değeri <xref:System.Activities.Statements.FlowNode> , içinde işlenmek üzere bir sonrakini belirler <xref:System.Activities.Statements.Flowchart> .

### <a name="using-the-flowdecision-designer"></a>Flowkarar tasarımcısını kullanma

**Flowkarar** Tasarımcısı **araç çubuğu** **kategorisinde bulunabilir** ve bu, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

**Flowkarar** Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içinde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.Activities.Statements.FlowDecision> , etkinlik içinde etiketlenmiş bir **karar** oluşturur <xref:System.Activities.Statements.Flowchart> . Tasarımcı üzerinde fare ve iki dal için **doğru** ve **yanlış** kare tutamaçları görüntülenir.

**Flowkarar** tasarımcısını ve diğer tasarımcıları **Akış Çizelgesine** sürükledikten sonra, yürütme sırasını belirtmek için düğümler birbirine bağlanabilir. Kaynak düğüm ( **doğru** ve **Hatalı** **flowkararı** dahil) ile bir hedef düğümün arasında bir bağlantı oluşturmak için, kaynak düğüm ve kare tutamaçları tasarımcısının her tarafında görünür. Kare tutamaçlarından birine tıklayın ve fare düğmesini, üzerine fare düğmesini basılı tutarak hedef düğümün etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve bir bağlantı, kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki düğüm arasında oluşturulmuş bir bağlantıdır.

' I belirten ifade, <xref:System.Activities.Statements.FlowDecision.Condition%2A> İpucu metninin "vb Ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **koşul** kutusuna yazılabilir.

### <a name="the-flowdecision-properties"></a>Flowkarar özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.FlowDecision> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Akış denetiminin hangi yolu aldığını belirleyen koşul.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Yanlış|Tatmin olursa akış denetimi tarafından alınan yol <xref:System.Activities.Statements.FlowDecision.Condition%2A> .|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Yanlış|Memnun değilse akış denetimi tarafından alınan yol <xref:System.Activities.Statements.FlowDecision.Condition%2A> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
