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
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851477"
---
# <a name="activity-views-legacy"></a>Etkinlik Görünümleri (Eski)
Tarafından sağlanan etkinliklerin birçoğu [!INCLUDE[wf](../includes/wf-md.md)] , iş akışlarının oluşturulduğu, eski sürümünde birçok tasarım görünümüne sahip olabilir [!INCLUDE[wfd1](../includes/wfd1-md.md)] . **Araç kutusundan** bir etkinlik Tasarımcısını Tasarım yüzeyine sürüklediğinizde ve bundan sonra etkinliği her seçtiğinizde, **iş akışı** menüsünü kullanarak veya seçili etkinliğe sağ tıklayarak farklı tasarım görünümleri arasında geçiş yapabilirsiniz. Ayrıca, işaretçiyi seçili bir etkinliğin adının üzerine getirdiğinizde, farklı görünümler arasında geçiş yapmak için kullanabileceğiniz bir aşağı açılan sekme kümesi görüntülenir.

 Her etkinliğin en az bir görünümü vardır; Bu, **araç kutusundan** bir etkinlik Tasarımcısını Tasarım yüzeyine sürüklediğinizde gösterilen varsayılan görünümüdür. Bu etkinlik varsayılan görünümü menülerde ve sekmede **Görünüm [etkinlik türü]** seçeneği olarak kullanılabilir (örneğin, **paralel görünüm**). Etkinliklerin çoğunda ek görünümler ve farklı etkinlikler farklı görünümlere sahip olabilir. Örneğin, [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) etkinliği Dengeleme görünümüne sahiptir ve [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) etkinliği bir olay görünümü içerir. Windows Workflow Foundation ile birlikte gelen etkinliklerin birçoğu, [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) ve bunlarla Ilişkili bir [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) görüntülemek Için, aynı görüntüleme **iptali işleyicisine** sahiptir ve hata tasarım görünümlerini **görüntüler** .

 Aşağıdaki tabloda her bir görünümün adı ve açıklaması listelenmektedir.

|Menü/sekme seçeneği|Description|
|----------------------|-----------------|
|**Görünüm [etkinlik türü]**|Seçilen etkinliğin varsayılan grafik temsilini görüntülemek için bu menüyü veya sekme seçeneğini belirleyin.|
|**Iptal Işleyicisini görüntüle**|Seçili etkinlikle ilişkili [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Hata Işleyicisini görüntüle**|Seçili etkinlikle ilişkili [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Dengeleme Işleyicisini görüntüle**|Seçili [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)Ile Ilişkili [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) 'yi görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|
|**Olay Işleyicisini görüntüle**|Seçili [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)Ile ilişkili [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) görüntülemek için bu menüyü veya sekme seçenek görünümünü seçin.|

 Benzer görünümler hakkında daha fazla bilgi için bkz. [sıralı Iş akışı görünümleri (eski)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski Iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md) [sıralı iş akışı görünümleri (eski)](../workflow-designer/sequential-workflow-views-legacy.md)
