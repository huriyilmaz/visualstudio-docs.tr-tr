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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656697"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı
@No__t_0 düğümü, belirtilen koşulun karşılanmasına bağlı olarak, denetimin iki alternatifden birine akışı için bir dal sağlayan koşullu bir düğümdür. Akışta ikiden fazla dal gerekiyorsa, bunun yerine <xref:System.Activities.Statements.FlowSwitch%601> kullanın.

## <a name="the-flowdecision-node"></a>Flowkarar düğümü
 Akış iki yola dallandırıtılabilir <xref:System.Activities.Statements.FlowDecision> kullanın. @No__t_0 düğüm <xref:System.Activities.Statements.FlowDecision.Condition%2A> ve olası iki sonuç ile ilişkili bir <xref:System.Activities.Statements.FlowNode> sahiptir: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A>. @No__t_0 değerlendirilir ve bu değerlendirmenin değeri <xref:System.Activities.Statements.Flowchart> içinde işlenecek sonraki <xref:System.Activities.Statements.FlowNode> belirler.

### <a name="using-the-flowdecision-designer"></a>Flowkarar tasarımcısını kullanma
 **Flowkarar** tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** sekmesine tıklanarak veya CTRL + tuşlarına basarak ) **araç**çubuğunun **akış çizelgesi** kategorisinde bulunabilir. ALT + X.)

 **Flowkarar** Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, <xref:System.Activities.Statements.Flowchart> etkinliği içinde etiketlenmiş <xref:System.Activities.Statements.FlowDecision> bir **karar** oluşturur. Tasarımcı üzerinde fare ve iki dal için **doğru** ve **yanlış** kare tutamaçları görüntülenir.

 **Flowkarar** tasarımcısını ve diğer tasarımcıları **Akış Çizelgesine**sürükledikten sonra, yürütme sırasını belirtmek için düğümler birbirine bağlanabilir. Kaynak düğüm ( **doğru** ve **Hatalı** **flowkararı**dahil) ile bir hedef düğümün arasında bir bağlantı oluşturmak için, kaynak düğüm ve kare tutamaçları tasarımcısının her tarafında görünür. Kare tutamaçlarından birine tıklayın ve fare düğmesini, üzerine fare düğmesini basılı tutarak hedef düğümün etrafında benzer şekilde görünen tutamaçlardan birine tıklayarak sürükleyin. Fare düğmesini bırakın ve bir bağlantı, kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki düğüm arasında oluşturulmuş bir bağlantıdır.

 @No__t_0 belirten ifade, ipucu metninin "VB ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **koşul** kutusuna yazılabilir.

### <a name="the-flowdecision-properties"></a>Flowkarar özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowDecision> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Akış denetiminin hangi yolu aldığını belirleyen koşul.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|@No__t_0 karşılandıysanız akış denetimi tarafından alınan yol.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|@No__t_0 karşılanmıyorsa akış denetimi tarafından alınan yol.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış](../workflow-designer/flowchart-activity-designers.md) çizelgesi [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [FlowSwitch \<T >](../workflow-designer/flowswitch-t-activity-designer.md)