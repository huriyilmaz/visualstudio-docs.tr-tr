---
title: İş Akışı Tasarımcısı-Flowkarar etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e405f82bcf33bc01ad07f1092879c17dec5849
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111443"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı

<xref:System.Activities.Statements.FlowDecision> düğümü, belirtilen koşulun karşılanmasına bağlı olarak, denetimin iki alternatifden birine akışı için bir dal sağlayan koşullu bir düğümdür. Akışta ikiden fazla dal gerekiyorsa, bunun yerine <xref:System.Activities.Statements.FlowSwitch%601> kullanın.

## <a name="the-flowdecision-node"></a>Flowkarar düğümü

Akış iki yola dallandırıtılabilir <xref:System.Activities.Statements.FlowDecision> kullanın. <xref:System.Activities.Statements.FlowDecision> düğüm <xref:System.Activities.Statements.FlowDecision.Condition%2A> ve olası iki sonuç ile ilişkili bir <xref:System.Activities.Statements.FlowNode> sahiptir: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> değerlendirilir ve bu değerlendirmenin değeri <xref:System.Activities.Statements.Flowchart>içinde işlenecek sonraki <xref:System.Activities.Statements.FlowNode> belirler.

### <a name="using-the-flowdecision-designer"></a>Flowkarar tasarımcısını kullanma

**Flowkarar** Tasarımcısı **araç çubuğu** **kategorisinde bulunabilir** ve bu, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL**+**alt**+**X**tuşuna basın.

**Flowkarar** Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içinde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu, <xref:System.Activities.Statements.Flowchart> etkinliği içinde etiketlenmiş <xref:System.Activities.Statements.FlowDecision> bir **karar** oluşturur. Tasarımcı üzerinde fare ve iki dal için **doğru** ve **yanlış** kare tutamaçları görüntülenir.

**Flowkarar** tasarımcısını ve diğer tasarımcıları **Akış Çizelgesine**sürükledikten sonra, yürütme sırasını belirtmek için düğümler birbirine bağlanabilir. Kaynak düğüm ( **doğru** ve **Hatalı** **flowkararı**dahil) ile bir hedef düğümün arasında bir bağlantı oluşturmak için, kaynak düğüm ve kare tutamaçları tasarımcısının her tarafında görünür. Kare tutamaçlarından birine tıklayın ve fare düğmesini, üzerine fare düğmesini basılı tutarak hedef düğümün etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve bir bağlantı, kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki düğüm arasında oluşturulmuş bir bağlantıdır.

<xref:System.Activities.Statements.FlowDecision.Condition%2A> belirten ifade, ipucu metninin "VB ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **koşul** kutusuna yazılabilir.

### <a name="the-flowdecision-properties"></a>Flowkarar özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.FlowDecision> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Akış denetiminin hangi yolu aldığını belirleyen koşul.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> karşılandıysanız akış denetimi tarafından alınan yol.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> karşılanmıyorsa akış denetimi tarafından alınan yol.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
