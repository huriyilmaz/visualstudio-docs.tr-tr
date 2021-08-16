---
title: İş Akışı Tasarımcısı - FlowSwitch &lt; T &gt; Etkinlik Tasarımcısı
description: FlowSwitch etkinliğinin, eşleşme ölçütüne göre denetim akışı için dallara dalılama <T> sağlayan koşullu bir düğüm olduğunu öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 6aa40da33fba5ae7f95e41fff6a2d905fc0585f64cab88d2d2cb0d4340cf8ccc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383787"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T> Etkinlik Tasarımcısı

Etkinlik, ikiden fazla alternatif dal gerektiğinde eşleşme ölçütüne göre denetim akışı <xref:System.Activities.Statements.FlowSwitch%601> için dallar sağlayan bir koşullu düğümdur. Akış dallama yalnızca iki yol gerektiriyorsa, bunun yerine <xref:System.Activities.Statements.FlowDecision> etkinliğini kullanın.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T> Etkinliği

Etkinlik <xref:System.Activities.Statements.FlowSwitch%601> değerlendirilirken <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> *T* türünde (genel parametre tarafından belirtilen) bir değer döndüren bir içerir. Etkinlik ayrıca, bu değerlendirmenin olası sonuçlarından bir nesne kümesine benzersiz bir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> eşleme belirten bir kümesi <xref:System.Activities.Statements.FlowNode> içerir. <xref:System.Activities.Statements.FlowNode>Yürütülen, *T* türünde nesnesi değerlendirilen değerinin değeriyle eşleşen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nesnedir. Eşleşme <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> alınmayacak bir durum için bir durum (isteğe bağlı olarak) sağlanmalıdır.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch Etkinlik \<T> Tasarımcısını Kullanma

**FlowSwitch \<T>** etkinlik tasarımcısı, araç kutusunun sol tarafındaki Araç Kutusu sekmesine tıklayarak  erişilen Araç Kutusu'İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**FlowSwitch \<T>** etkinlik tasarımcısı Araç Kutusundan sürüklenip **flowchart** etkinlik tasarımcısında İş Akışı Tasarımcısı **yüzeyine** bırakılır. değerlendirmesinde **elde** edilen türü (ile kodda ilişkili, genel parametresiyle ilişkili) belirtmek için görüntüleyen Türleri Seçin <xref:System.Activities.Statements.FlowSwitch%601> penceresini <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> kullanın. Bu yordam, etkinlik <xref:System.Activities.Statements.FlowSwitch%601> içinde Switch **etiketli bir** etkinlik <xref:System.Activities.Statements.Flowchart> oluşturur. , Özellikler penceresinin İfade kutusuna, ipucu metninin "VB ifadesi girin" olarak <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> yazarak yazabilirsiniz.  

Fareyle **FlowSwitch \<T> etkinlik** tasarımcısının üzerine gelen fare, bağlantı için kullanılan kare tutamaçların <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kenarlarında görünmesine neden olur. **FlowSwitch<tasarımcısını \>** ve diğer etkinlik tasarımcılarını **Flowchart'a** sürükledikten sonra, temsil edecekleri nesneler yürütme sırası belirtmek için birbirine <xref:System.Activities.Activity> bağlanmaya hazırdır. ile ilişkili bir tane oluşturmak için <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> <xref:System.Activities.Statements.FlowSwitch%601> **FlowSwitch<\> T'nin** çevresinde yer alan kare büyük/küçük harf tanıtıcılarından birini tıklatın ve fare tasarımcının üzerine geldiğinde hedef etkinliğin etrafında benzer şekilde görünen tutamaçlardan birini sürükleyin (fare düğmesini basılı tutarak). Fare düğmesini bırakın ve **FlowSwitch \>** T<hedef tasarımcıya bir ok bırakın. Bu durum için varsayılan değer okta görüntülenir ve Özellikler penceresinin Durum **kutusunda** **düzenlenebilir.**

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T> Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.FlowSwitch%601> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Yürütme yolunda hangisine geçiş yapmak üzere <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> değerlendirilecek ifadeyi belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Yanlış|bir nesne kümesine değerlendirilmeden elde edilen olası sonuçlardan <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> benzersiz bir eşleme <xref:System.Activities.Statements.FlowNode> belirtir.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|değerlendirmesi nesnesinde yer alan <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> değerlerden biri ile eşleşmezken eşlemeyi <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
