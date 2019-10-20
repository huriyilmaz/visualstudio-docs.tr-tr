---
title: İş Akışı Tasarımcısı-FlowSwitch <T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f167f46a2ed118e8781f66e4a781d4a3ef95b0d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650401"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch \<T > etkinlik Tasarımcısı

@No__t_0 etkinliği, ikiden fazla alternatif dal gerektiğinde, eşleşme ölçütüne göre denetim akışı için dallandırma sağlayan koşullu bir düğümdür. Akış dallandırma yalnızca iki yol gerektiriyorsa, bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T > etkinliği

@No__t_0 etkinliği, değerlendirildiğinde *t* türünde bir değer döndüren bir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> içerir (genel parametresiyle belirtilir). Etkinlik Ayrıca, bu değerlendirmenin olası sonuçlarından bir dizi <xref:System.Activities.Statements.FlowNode> nesneye benzersiz bir eşleme belirten <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> bir kümesini içerir. Yürütülen <xref:System.Activities.Statements.FlowNode>, nesne türü *t* , değerlendirilen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değeriyle eşleşen bir nesnedir. Bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> durumu (isteğe bağlı olarak), hiçbir eşleşme alınmadıysa durum için sağlanır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T > etkinlik tasarımcısını kullanma

**FlowSwitch \<T >** etkinlik tasarımcısı, iş akışı Tasarımcısı 'nin sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen, **araç çubuğu** **kategorisinde bulunabilir** . Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

**FlowSwitch \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içindeki iş akışı Tasarımcısı yüzeyine bırakılabilir. @No__t_2 değerlendirmeden elde edilen türü belirtmek için görüntülenen **türleri Seç** penceresini kullanın (genel parametresine göre <xref:System.Activities.Statements.FlowSwitch%601> ile ilişkilidir). Bu yordam, <xref:System.Activities.Statements.Flowchart> etkinliğinde **anahtar** etiketli <xref:System.Activities.Statements.FlowSwitch%601> bir etkinlik oluşturur. @No__t_0, ipucu metninin "VB ifadesi gir" olarak tıklanarak **Özellikler** penceresinin **ifade** kutusuna yazılabilir.

**@No__t_1T >** etkinlik Tasarımcısı üzerinde fare, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> bağlantı kurmak için kullanılan kare tutamaçlarının kenarları etrafında görünmesini sağlamak için. **FlowSwitch < T \>** etkinlik Tasarımcısı ve diğer etkinlik tasarımcılarını **Akış Çizelgesine**sürükledikten sonra temsil ettikleri <xref:System.Activities.Activity> nesneleri, yürütme sırasını belirtmek için birlikte bağlanmaya hazırlardır. @No__t_1 ilişkili <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> birini oluşturmak için, **akışların FlowSwitch < t \>** çevresi üzerinde yer alan ve sürükleyin (fare düğmesini basılı tutarak), benzer bir şekilde görünen tanıtıcıların birine fare tasarımcısının üzerine geldiğinde hedef etkinlik. Fare düğmesini ve **FlowSwitch < T \>** , bu durumu temsil eden hedef tasarlayıcısından bir ok olarak bırakın. Bu örnek için varsayılan değer ok üzerinde görüntülenir ve **Özellikler** penceresinin **durum** kutusunda düzenlenebilir.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Yürütmenin yolunda ne <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> hangilerinin ekleneceğini belirlemekte değerlendirilen ifadeyi belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|@No__t_0 bir <xref:System.Activities.Statements.FlowNode> nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan benzersiz bir eşleme belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|@No__t_0 değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> nesnesinde bulunan değerlerden biriyle eşleşmezse eşlemeyi belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)