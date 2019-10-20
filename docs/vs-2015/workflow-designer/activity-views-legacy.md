---
title: Etkinlik görünümleri (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7d8a13890814b56865200acf95c8e0565b52b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655216"
---
# <a name="activity-views-legacy"></a>Etkinlik Görünümleri (Eski)
@No__t_0 tarafından sağlanan etkinliklerin birçoğu, iş akışlarının oluştuğu, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] birçok tasarım görünümüne sahip olabilir. **Araç kutusundan** bir etkinlik Tasarımcısını Tasarım yüzeyine sürüklediğinizde ve bundan sonra etkinliği seçtiğinizde, **iş akışı** menüsünü kullanarak veya seçili öğesine sağ tıklayarak farklı tasarım görünümleri arasında geçiş yapabilirsiniz. etkinlik. Ayrıca, işaretçiyi seçili bir etkinliğin adının üzerine getirdiğinizde, farklı görünümler arasında geçiş yapmak için kullanabileceğiniz bir aşağı açılan sekme kümesi görüntülenir.

 Her etkinliğin en az bir görünümü vardır; Bu, **araç kutusundan** bir etkinlik Tasarımcısını Tasarım yüzeyine sürüklediğinizde gösterilen varsayılan görünümüdür. Bu etkinlik varsayılan görünümü menülerde ve sekmede **Görünüm [etkinlik türü]** seçeneği olarak kullanılabilir (örneğin, **paralel görünüm**). Etkinliklerin çoğunda ek görünümler ve farklı etkinlikler farklı görünümlere sahip olabilir. Örneğin, [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) etkinliği Dengeleme görünümüne sahiptir ve [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) etkinliği bir olay görünümü içerir. Windows Workflow Foundation ile birlikte gelen etkinliklerin birçoğu, [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) ve bunlarla Ilişkili bir [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) görüntülemek Için, aynı görüntüleme **iptali işleyicisine** sahiptir ve hata tasarım görünümlerini **görüntüler** .

 Aşağıdaki tabloda her bir görünümün adı ve açıklaması listelenmektedir.

|Menü/sekme seçeneği|Açıklama|
|----------------------|-----------------|
|**Görünüm [etkinlik türü]**|Seçilen etkinliğin varsayılan grafik temsilini görüntülemek için bu menüyü veya sekme seçeneğini belirleyin.|
|**Iptal Işleyicisini görüntüle**|Seçili etkinlikle ilişkili [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Hata Işleyicisini görüntüle**|Seçili etkinlikle ilişkili [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Dengeleme Işleyicisini görüntüle**|Seçili [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)Ile Ilişkili [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) 'yi görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Olay Işleyicisini görüntüle**|Seçili [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)Ile ilişkili [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|

 Benzer görünümler hakkında daha fazla bilgi için bkz. [sıralı Iş akışı görünümleri (eski)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski Iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md) [sıralı iş akışı görünümleri (eski)](../workflow-designer/sequential-workflow-views-legacy.md)