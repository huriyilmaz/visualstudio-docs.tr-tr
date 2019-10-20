---
title: FlowSwitch &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656638"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt;T &gt; etkinlik Tasarımcısı
@No__t_0 etkinliği, ikiden fazla alternatif dal gerektiğinde, eşleşme ölçütüne göre denetim akışı için dallandırma sağlayan koşullu bir düğümdür. Akış dallandırma yalnızca iki yol gerektiriyorsa, bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T > etkinliği
 @No__t_0 etkinliği, değerlendirildiğinde *t* türünde bir değer döndüren bir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> içerir (genel parametresiyle belirtilir). Etkinlik Ayrıca, bu değerlendirmenin olası sonuçlarından bir dizi <xref:System.Activities.Statements.FlowNode> nesneye benzersiz bir eşleme belirten <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> bir kümesini içerir. Yürütülen <xref:System.Activities.Statements.FlowNode>, nesne türü *t* , değerlendirilen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değeriyle eşleşen bir nesnedir. Bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> durumu (isteğe bağlı olarak), hiçbir eşleşme alınmadıysa durum için sağlanır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T > etkinlik tasarımcısını kullanma
 **FlowSwitch \<T >** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] 'nın sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç**çubuğunun **akış çizelgesi** kategorisinde bulunabilir (alternatif olarak, **araç çubuğu** ' nu seçin). **Görünüm** menüsünden veya Ctrl + Alt + X.)

 **FlowSwitch \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip bir **akış çizelgesi** etkinlik Tasarımcısı içindeki [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. @No__t_2 değerlendirmeden elde edilen türü belirtmek için görüntülenen **türleri Seç** penceresini kullanın (genel parametresine göre <xref:System.Activities.Statements.FlowSwitch%601> ile ilişkilidir). Bu yordam, <xref:System.Activities.Statements.Flowchart> etkinliğinde **anahtar** etiketli <xref:System.Activities.Statements.FlowSwitch%601> bir etkinlik oluşturur. @No__t_0, ipucu metninin "VB ifadesi gir" olarak tıklanarak **Özellikler** penceresinin **ifade** kutusuna yazılabilir.

 **@No__t_1T >** etkinlik Tasarımcısı üzerinde fare, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> bağlantı kurmak için kullanılan kare tutamaçlarının kenarları etrafında görünmesini sağlamak için. **FlowSwitch < T \>** etkinlik Tasarımcısı ve diğer etkinlik tasarımcılarını **Akış Çizelgesine**sürükledikten sonra temsil ettikleri <xref:System.Activities.Activity> nesneleri, yürütme sırasını belirtmek için birlikte bağlanmaya hazırlardır. @No__t_1 ilişkili <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> birini oluşturmak için, **akışların FlowSwitch \<T** çevre bölümünde yer alan her bir kareye tıklayın > ve bu şekilde bir benzer şekilde görünen tutamaçlardan birine sürükleyin (fare düğmesini basılı tutarak) fare tasarımcısının üzerine geldiğinde hedef etkinlik. Fare düğmesini ve **FlowSwitch \<T >** , bu durumu temsil eden hedef tasarımcı ' ya bir ok olarak bırakın. Bu örnek için varsayılan değer ok üzerinde görüntülenir ve **Özellikler** penceresinin **durum** kutusunda düzenlenebilir.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T > Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Yürütmenin yolunda ne <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> hangilerinin ekleneceğini belirlemekte değerlendirilen ifadeyi belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|@No__t_0 bir <xref:System.Activities.Statements.FlowNode> nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan benzersiz bir eşleme belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|@No__t_0 değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> nesnesinde bulunan değerlerden biriyle eşleşmezse eşlemeyi belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış](../workflow-designer/flowchart-activity-designers.md) çizelgesi [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [flowkararı](../workflow-designer/flowdecision-activity-designer.md)