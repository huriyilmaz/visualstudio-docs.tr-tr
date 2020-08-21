---
title: İş Akışı Tasarımcısı-FlowSwitch &lt; T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6637682bd6ba649f27c1a53f3b1448629f03736
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711579"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T> Etkinlik Tasarımcısı

<xref:System.Activities.Statements.FlowSwitch%601>Etkinlik, iki alternatif dal gerektiğinde, eşleşme ölçütüne göre denetim akışı için dallandırma sağlayan koşullu bir düğümdür. Akış dallandırma yalnızca iki yol gerektiriyorsa, <xref:System.Activities.Statements.FlowDecision> bunun yerine etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T> etkinliği

<xref:System.Activities.Statements.FlowSwitch%601>Etkinlik, <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değerlendirildiğinde *T* türünde bir değer (genel parametresiyle belirtilir) döndüren bir içerir. Etkinlik ayrıca bir kümesini içerir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> ve bu değerlendirmenin olası sonuçlarından bir nesne kümesine benzersiz bir eşleme belirtir <xref:System.Activities.Statements.FlowNode> . <xref:System.Activities.Statements.FlowNode>Yürütülen nesne, değerlendirilen değeri, değerlendirilen değeriyle eşleşen *T* bir nesnedir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> durum (isteğe bağlı olarak), hiçbir eşleşme alınmamıştır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T> etkinlik tasarımcısını kullanma

** \<T> FlowSwitch** etkinlik Tasarımcısı, iş akışı Tasarımcısı 'In sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç çubuğu** **kategorisinde bulunabilir** . Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

**FlowSwitch \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içinde iş akışı Tasarımcısı yüzeyine bırakılabilir. Değerlendirilmeden elde edilen türü belirtmek için görüntülenen **türleri Seç** penceresini kullanın (genel parametresine göre ile ilişkili kod ile ilişkilendirilir <xref:System.Activities.Statements.FlowSwitch%601> ) <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Bu yordam <xref:System.Activities.Statements.FlowSwitch%601> , etkinlik Içinde **anahtar** etiketli bir etkinlik oluşturur <xref:System.Activities.Statements.Flowchart> . , <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> İpucu metninin "vb Ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **ifade** kutusuna yazılabilir.

**FlowSwitch \<T> ** etkinlik Tasarımcısı üzerinde fare, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kenarları etrafında görüntülenecek şekilde bağlantı kurmak için kullanılan kare tutamaçlarının oluşmasına neden olur. **FlowSwitch<T \> ** etkinlik tasarımcısını ve diğer etkinlik tasarımcılarını **Akış Çizelgesine**sürükledikten sonra <xref:System.Activities.Activity> temsil ettikleri nesneler, yürütme sırasını belirtmek için birlikte bağlanmaya hazırlarlar. İle ilişkili aşağıdakilerden birini oluşturmak için <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> <xref:System.Activities.Statements.FlowSwitch%601> , akışın çevreninin çevresi üzerinde yer alan bir kare, **<T \> ** ve sürükleyin (fare düğmesini basılı tutarak), fare tasarımcısının üzerine geldiğinde hedef etkinlik etrafında benzer şekilde görünen tutamaçlardan birine tıklayın. Fare düğmesini ve **FlowSwitch<T \> ** ' den, bu durumu temsil eden hedef tasarımcı ' ya bir ok işareti olarak bırakın. Bu örnek için varsayılan değer ok üzerinde görüntülenir ve **Özellikler** penceresinin **durum** kutusunda düzenlenebilir.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Hangisinin yürütme yolunda ne kadar geçiş kullanacağını belirleyen değerlendirilen ifadeyi belirtir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Yanlış|Bir nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan benzersiz bir eşleme belirtir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> <xref:System.Activities.Statements.FlowNode> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|Öğesinin değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nesnede bulunan değerlerden biriyle eşleşmezse eşlemeyi belirtir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
