---
title: İş Akışı Tasarımcısı - Akış Çizelgesi Etkinlik Tasarımcısı
description: Karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için Flowchart etkinliğini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 948d4536f28440671fdba2a7a9931e0da66d7834
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155206"
---
# <a name="flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı

Etkinlik, <xref:System.Activities.Statements.Flowchart> karmaşık akış denetimlerini tanımlayan ve yöneten iş akışları oluşturmak için kullanılır. , <xref:System.Activities.Statements.Flowchart> kodda veya kod kullanılarak İş Akışı Tasarımcısı. Bu konu başlığında, İş Akışı Tasarımcısı belgelemektedir. İş İş Akışı Tasarımcısı tasarımcısı, geliştiricilerin iş akışlarını doğal bir şekilde yazmalarını sağlar.

## <a name="the-flowchart-activity"></a>Flowchart Etkinliği

, iş akışı başlatıldığında yürütülen ve rastgele döngüler oluşturmak veya yürütme akışını herhangi bir zamanda iş akışında başka bir yere aktarmak için bağlı bir ağ kullanan benzersiz <xref:System.Activities.Statements.Flowchart> <xref:System.Activities.Statements.Flowchart.StartNode%2A> bir <xref:System.Activities.Statements.Flowchart.Nodes%2A> belirtir.

### <a name="using-the-flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı'nı kullanma

Flowchart etkinlik tasarımcısı, araç  kutusunun Araç Kutusu sekmesine tıklayarak erişilen  Araç Kutusu'İş Akışı Tasarımcısı.   Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**Flowchart** etkinlik tasarımcısı **Araç** Kutusundan sürüklenerek etkinlik tasarımcılarının normalde kök etkinlik olarak veya başka bir denetim akışı etkinliğinin alt etkinliği olarak yerleştirildikten sonra İş Akışı Tasarımcısı yüzeyine bırakılır. **Flowchart etkinlik** tasarımcısı boş bir İş Akışı Tasarımcısı yüzeyine bırakılırsa, varsayılan olarak yürütmeyi başlatan başlangıç düğümünün yeşil top olarak temsil edilen genişletilmiş bir görünümde kendisini sunan bir etkinlik <xref:System.Activities.Statements.Flowchart> oluşturur. Flowchart **etkinlik tasarımcısı** başka bir denetim akışı etkinliğine bırakılırsa, Flowchart etkinlik tasarımcısına çift tıklarsanız genişletilebilir bir simge durumuna **küçültülmüş görünümde** kendini gösterir. Araç **Kutusu'nda yer alan herhangi** bir etkinlik, diğer denetim akışı etkinlikleri de dahil olmak üzere doğrudan **Flowchart** etkinlik tasarımcısına sürüklenebilirsiniz.

Çeşitli etkinlik tasarımcıları İş Akışı Tasarımcısı tuvale sürüklendikten sonra temsil edecekleri nesneler birlikte bağlanarak <xref:System.Activities.Activity> yürütme sırası belirtebilirsiniz. Bir kaynak etkinlik ve hedef etkinlik arasında bağlantı oluşturmak için fareyle kaynak etkinliğin tasarımcısının üzerine gelir ve her tarafında kare tanıtıcılar görünür. Kare tutamaçlardan birini tıklatın ve fare düğmesini fareyle üzerine gelindiğinde hedef etkinliğin etrafında benzer şekilde görünen tutamaçlardan biri olacak şekilde sürükleyerek sürükleyin. Fare düğmesini bırakın ve kaynak tasarımcıdan hedef tasarımcıya ok olarak temsil edilen bu iki etkinlik arasında bir bağlantı oluşturulur.

### <a name="flowchart-activity-properties"></a>Akış Çizelgesi Etkinlik Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.Flowchart> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının görünen adını belirtir. Varsayılan değer Flowchart'tır. Değer, Özellikler penceresinde veya **doğrudan** etkinlik tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Yanlış|Durumu alt etkinlikleri arasında paylaşmak için bu <xref:System.Activities.Statements.Flowchart> kapsamda yer alan değişkenlerin koleksiyonu.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Yanlış|başlatıldığında <xref:System.Activities.Statements.FlowNode> yürütülen <xref:System.Activities.Statements.Flowchart> .|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Yanlış|içinde nesne <xref:System.Activities.Statements.FlowNode> koleksiyonunu <xref:System.Activities.Statements.Flowchart> içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
