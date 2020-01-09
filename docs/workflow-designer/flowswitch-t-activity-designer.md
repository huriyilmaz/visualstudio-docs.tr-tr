---
title: İş Akışı Tasarımcısı-FlowSwitch<T> etkinlik Tasarımcısı
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
ms.openlocfilehash: 8271100936b9cf70e17c0e6279297d583714f018
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597158"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > etkinlik Tasarımcısı

<xref:System.Activities.Statements.FlowSwitch%601> etkinliği, ikiden fazla alternatif dal gerektiğinde, eşleşme ölçütüne göre denetim akışı için dallandırma sağlayan koşullu bir düğümdür. Akış dallandırma yalnızca iki yol gerektiriyorsa, bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > etkinliği

<xref:System.Activities.Statements.FlowSwitch%601> etkinliği, değerlendirildiğinde *t* türünde bir değer döndüren bir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> içerir (genel parametresiyle belirtilir). Etkinlik Ayrıca, bu değerlendirmenin olası sonuçlarından bir dizi <xref:System.Activities.Statements.FlowNode> nesneye benzersiz bir eşleme belirten <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>bir kümesini içerir. Yürütülen <xref:System.Activities.Statements.FlowNode>, nesne türü *t* , değerlendirilen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>değeriyle eşleşen bir nesnedir. Bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> durumu (isteğe bağlı olarak), hiçbir eşleşme alınmadıysa durum için sağlanır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch\<T > etkinlik tasarımcısını kullanma

**FlowSwitch\<t >** etkinlik tasarımcısı, iş akışı Tasarımcısı 'nin sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç çubuğu** **kategorisinde bulunabilir** . Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL**+**alt**+**X**tuşuna basın.

**FlowSwitch\<t >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içindeki iş akışı Tasarımcısı yüzeyine bırakılabilir. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>değerlendirmeden elde edilen türü belirtmek için görüntülenen **türleri Seç** penceresini kullanın (genel parametresine göre <xref:System.Activities.Statements.FlowSwitch%601> ile ilişkilidir). Bu yordam, <xref:System.Activities.Statements.Flowchart> etkinliğinde **anahtar** etiketli <xref:System.Activities.Statements.FlowSwitch%601> bir etkinlik oluşturur. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, ipucu metninin "VB ifadesi gir" olarak tıklanarak **Özellikler** penceresinin **ifade** kutusuna yazılabilir.

**\<t >** etkinlik Tasarımcısı üzerinde fare, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> bağlantı kurmak için kullanılan kare tutamaçlarının kenarlarının etrafında görünmesini sağlamak için. **FlowSwitch < T\>** etkinlik Tasarımcısı ve diğer etkinlik tasarımcılarını **Akış Çizelgesine**sürükledikten sonra temsil ettikleri <xref:System.Activities.Activity> nesneleri, yürütme sırasını belirtmek için birlikte bağlanmaya hazırlardır. <xref:System.Activities.Statements.FlowSwitch%601>ilişkili <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> birini oluşturmak için, **akışların FlowSwitch < t\>** çevresi üzerinde yer alan ve sürükleyin (fare düğmesini basılı tutarak) fare tasarımcısının üzerine geldiğinde hedef etkinlik etrafında benzer şekilde görünen tutamaçlardan birine tıklayın. Fare düğmesini ve **FlowSwitch < T\>** , bu durumu temsil eden hedef tasarlayıcısından bir ok olarak bırakın. Bu örnek için varsayılan değer ok üzerinde görüntülenir ve **Özellikler** penceresinin **durum** kutusunda düzenlenebilir.

### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Yürütmenin yolunda ne <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> hangilerinin ekleneceğini belirlemekte değerlendirilen ifadeyi belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> bir <xref:System.Activities.Statements.FlowNode> nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan benzersiz bir eşleme belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> nesnesinde bulunan değerlerden biriyle eşleşmezse eşlemeyi belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
