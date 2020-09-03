---
title: Flowkarar etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b93d88462d5e3984b06c671455439e9bd2b07c5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656697"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı
<xref:System.Activities.Statements.FlowDecision>Düğüm, belirtilen koşulun karşılanmasına bağlı olarak, denetimin iki alternatifden birine akışı için bir dal sağlayan koşullu bir düğümdür. Akışta ikiden fazla dal gerekiyorsa, <xref:System.Activities.Statements.FlowSwitch%601> bunun yerine kullanın.

## <a name="the-flowdecision-node"></a>Flowkarar düğümü
 <xref:System.Activities.Statements.FlowDecision>Akışın iki yola dallandırılmasına yol açabilir. Bir <xref:System.Activities.Statements.FlowDecision> düğüm, <xref:System.Activities.Statements.FlowDecision.Condition%2A> ve <xref:System.Activities.Statements.FlowNode> her iki olası sonuç ile ilişkili bir ve içerir: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A> . <xref:System.Activities.Statements.FlowDecision.Condition%2A>Değerlendirilir ve bu değerlendirmenin değeri <xref:System.Activities.Statements.FlowNode> , içinde işlenmek üzere bir sonrakini belirler <xref:System.Activities.Statements.Flowchart> .

### <a name="using-the-flowdecision-designer"></a>Flowkarar tasarımcısını kullanma
 **Flowkarar** Tasarımcısı, araç çubuğunda **bulunan araç kutusu sekmesine** tıklanarak erişilen **Toolbox** **Flowchart** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin) araç kutusu kategorisinde bulunabilir.

 **Flowkarar** Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] bir **akış çizelgesi** etkinlik Tasarımcısı içinde yüzeyine bırakılabilir. Bu <xref:System.Activities.Statements.FlowDecision> , etkinlik içinde etiketlenmiş bir **karar** oluşturur <xref:System.Activities.Statements.Flowchart> . Tasarımcı üzerinde fare ve iki dal için **doğru** ve **yanlış** kare tutamaçları görüntülenir.

 **Flowkarar** tasarımcısını ve diğer tasarımcıları **Akış Çizelgesine**sürükledikten sonra, yürütme sırasını belirtmek için düğümler birbirine bağlanabilir. Kaynak düğüm ( **doğru** ve **Hatalı** **flowkararı**dahil) ile bir hedef düğümün arasında bir bağlantı oluşturmak için, kaynak düğüm ve kare tutamaçları tasarımcısının her tarafında görünür. Kare tutamaçlarından birine tıklayın ve fare düğmesini, üzerine fare düğmesini basılı tutarak hedef düğümün etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve bir bağlantı, kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki düğüm arasında oluşturulmuş bir bağlantıdır.

 ' I belirten ifade, <xref:System.Activities.Statements.FlowDecision.Condition%2A> İpucu metninin "vb Ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **koşul** kutusuna yazılabilir.

### <a name="the-flowdecision-properties"></a>Flowkarar özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowDecision> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Akış denetiminin hangi yolu aldığını belirleyen koşul.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Yanlış|Tatmin olursa akış denetimi tarafından alınan yol <xref:System.Activities.Statements.FlowDecision.Condition%2A> .|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Yanlış|Memnun değilse akış denetimi tarafından alınan yol <xref:System.Activities.Statements.FlowDecision.Condition%2A> .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış](../workflow-designer/flowchart-activity-designers.md) çizelgesi [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)