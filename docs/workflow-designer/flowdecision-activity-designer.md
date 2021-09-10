---
title: İş Akışı Tasarımcısı - FlowDecision Etkinlik Tasarımcısı
description: FlowDecision düğümünün, denetim akışı için iki alternatifden birini sağlayan koşullu düğüm olduğunu öğrenin.
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
ms.openlocfilehash: 44afcb360f8517dd2ff8f30a76bb9a809b0da450
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963735"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı

Düğüm, belirtilen koşulun karşı olup olmadığını temel alarak denetim akışı için bir dal sağlayan iki <xref:System.Activities.Statements.FlowDecision> alternatiften biri olan koşullu düğüm olur. Akış ikiden fazla dal gerektiriyorsa bunun yerine <xref:System.Activities.Statements.FlowSwitch%601> kullanın.

## <a name="the-flowdecision-node"></a>FlowDecision Düğümü

Akışın <xref:System.Activities.Statements.FlowDecision> iki yola dallandırılana kadar kullanabileceğiniz zaman kullanın. Bir <xref:System.Activities.Statements.FlowDecision> düğümün iki <xref:System.Activities.Statements.FlowDecision.Condition%2A> olası <xref:System.Activities.Statements.FlowNode> sonucun her biri ile ilişkilendirilmiş bir ve vardır: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A> . <xref:System.Activities.Statements.FlowDecision.Condition%2A>değerlendirilir ve bu değerlendirmenin değeri içinde işlenecek sonraki değeri <xref:System.Activities.Statements.FlowNode> <xref:System.Activities.Statements.Flowchart> belirler.

### <a name="using-the-flowdecision-designer"></a>FlowDecision Tasarımcısını Kullanma

**FlowDecision** tasarımcısı, araç kutusunun  Araç Kutusu sekmesine tıklayarak erişilen Araç **Kutusu'İş Akışı Tasarımcısı.** Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**FlowDecision** tasarımcısı Araç Kutusundan sürüklenip **flowchart** etkinlik tasarımcısında İş Akışı Tasarımcısı **yüzeyine** bırakılır. Bu işlem etkinlik <xref:System.Activities.Statements.FlowDecision> içinde **Karar etiketli** bir <xref:System.Activities.Statements.Flowchart> oluşturur. Fareyle tasarımcının üzerine, **iki dal için True** ve **False** kare tutamaçları görünür.

**FlowDecision tasarımcısını** ve diğer tasarımcıları **Flowchart'a** sürükledikten sonra düğümler birlikte bağlanarak yürütme sırası belirt olabilir. Bir kaynak düğüm **(FlowDecision'un** **True** ve **False** dalları dahil) ile hedef düğüm arasında bir bağlantı oluşturmak için fareyle kaynak düğümün tasarımcısının üzerine fare ve her tarafında kare tanıtıcılar görünür. Kare tutamaçlardan birini tıklatın ve fare düğmesini fareyle üzerine geldiğinde hedef düğümün etrafında benzer şekilde görünen tutamaçlardan biri olacak şekilde sürükleyerek sürükleyin. Fare düğmesini bırakın ve kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki düğüm arasında bir bağlantı oluşturulur.

özellikler penceresinin Koşul kutusuna ipucu metninin "VB ifadesi girin" yazarak yazılacağını söyleyen <xref:System.Activities.Statements.FlowDecision.Condition%2A> ifade.  

### <a name="the-flowdecision-properties"></a>FlowDecision Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.FlowDecision> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Akış denetimi için hangi yolu takip etmek olduğunu belirleyen koşul.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Yanlış|Eğer karşılandı ise akış denetimi <xref:System.Activities.Statements.FlowDecision.Condition%2A> tarafından alınan yol.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Yanlış|Akışın karşılanmazsa akış denetimi <xref:System.Activities.Statements.FlowDecision.Condition%2A> tarafından alınan yol.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
