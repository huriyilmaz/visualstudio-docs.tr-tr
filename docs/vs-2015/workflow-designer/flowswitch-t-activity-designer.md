---
title: FlowSwitch &lt; T &gt; etkinlik Tasarımcısı | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656638"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt; T &gt; etkinlik Tasarımcısı
<xref:System.Activities.Statements.FlowSwitch%601>Etkinlik, iki alternatif dal gerektiğinde, eşleşme ölçütüne göre denetim akışı için dallandırma sağlayan koşullu bir düğümdür. Akış dallandırma yalnızca iki yol gerektiriyorsa, <xref:System.Activities.Statements.FlowDecision> bunun yerine etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T> etkinliği
 <xref:System.Activities.Statements.FlowSwitch%601>Etkinlik, <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değerlendirildiğinde *T* türünde bir değer (genel parametresiyle belirtilir) döndüren bir içerir. Etkinlik ayrıca bir kümesini içerir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> ve bu değerlendirmenin olası sonuçlarından bir nesne kümesine benzersiz bir eşleme belirtir <xref:System.Activities.Statements.FlowNode> . <xref:System.Activities.Statements.FlowNode>Yürütülen nesne, değerlendirilen değeri, değerlendirilen değeriyle eşleşen *T* bir nesnedir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> durum (isteğe bağlı olarak), hiçbir eşleşme alınmamıştır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T> etkinlik tasarımcısını kullanma
 **FlowSwitch \<T> ** etkinlik Tasarımcısı, ' ın sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen **araç**çubuğunun **akış çizelgesi** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu seçin veya Ctrl + Alt + X ' i seçin.)

 ** \<T> FlowSwitch** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] bir **akış çizelgesi** etkinlik Tasarımcısı içinde yüzeyine bırakılabilir. Değerlendirilmeden elde edilen türü belirtmek için görüntülenen **türleri Seç** penceresini kullanın (genel parametresine göre ile ilişkili kod ile ilişkilendirilir <xref:System.Activities.Statements.FlowSwitch%601> ) <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Bu yordam <xref:System.Activities.Statements.FlowSwitch%601> , etkinlik Içinde **anahtar** etiketli bir etkinlik oluşturur <xref:System.Activities.Statements.Flowchart> . , <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> İpucu metninin "vb Ifadesi girin" ifadesini tıklatarak **Özellikler** penceresinin **ifade** kutusuna yazılabilir.

 **FlowSwitch \<T> ** etkinlik Tasarımcısı üzerinde fare, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kenarları etrafında görüntülenecek şekilde bağlantı kurmak için kullanılan kare tutamaçlarının oluşmasına neden olur. **FlowSwitch<T \> ** etkinlik tasarımcısını ve diğer etkinlik tasarımcılarını **Akış Çizelgesine**sürükledikten sonra <xref:System.Activities.Activity> temsil ettikleri nesneler, yürütme sırasını belirtmek için birlikte bağlanmaya hazırlarlar. İle ilişkili aşağıdakilerden birini oluşturmak için <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> <xref:System.Activities.Statements.FlowSwitch%601> , ** \<T> akışın** çevre birimi üzerindeki kare içinden birine tıklayın ve fare tasarımcı üzerinde dolaştığında hedef etkinlik etrafında benzer şekilde görünen tutamaçlardan birine sürükleyin (fare düğmesini basılı tutarak). Fare düğmesini bırakın ve **FlowSwitch \<T> ** 'den hedef tasarımcı 'ya bir ok bu durumu temsil eder. Bu örnek için varsayılan değer ok üzerinde görüntülenir ve **Özellikler** penceresinin **durum** kutusunda düzenlenebilir.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T> Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Hangisinin yürütme yolunda ne kadar geçiş kullanacağını belirleyen değerlendirilen ifadeyi belirtir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Yanlış|Bir nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan benzersiz bir eşleme belirtir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> <xref:System.Activities.Statements.FlowNode> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|Öğesinin değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nesnede bulunan değerlerden biriyle eşleşmezse eşlemeyi belirtir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış](../workflow-designer/flowchart-activity-designers.md) çizelgesi [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [flowkararı](../workflow-designer/flowdecision-activity-designer.md)