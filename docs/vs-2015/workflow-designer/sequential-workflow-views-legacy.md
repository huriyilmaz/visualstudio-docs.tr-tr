---
title: Sıralı Iş akışı görünümleri (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846211"
---
# <a name="sequential-workflow-views-legacy"></a>Sıralı İş Akışı Görünümleri (Eski)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] veya ' i [!INCLUDE[wfd1](../includes/wfd1-md.md)] hedeflemek için kullanılabilecek bir eski sağlar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 , [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] Tanıdık kullanıcı arabirimini kullanarak uygulamaları grafiksel olarak oluşturmak için bir yol sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[wf](../includes/wf-md.md)] uygulamalar, etkinlik olarak adlandırılan iş akışı işlemi adımlarından oluşur. Bir iş akışı oluşturmak için, ilgili etkinlik tasarımcılarını **araç kutusu** 'ndan tasarım yüzeyine sürükleyerek tasarım yüzeyine etkinlik oluşturun.

 Bir [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)olan sıralı bir iş akışı oluşturduğunuzda, iş akışının üç görünümü kullanılabilir. Bu görünümlere, **Iş akışı** menüsünden ve tasarım yüzeyindeki bağlam menüsünden erişilebilir.

 Aşağıdaki tabloda her bir görünümün adı ve açıklaması listelenmektedir.

|Menü/sekme seçeneği|Description|
|----------------------|-----------------|
|**SequentialWorkflow görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünde **Görünüm SequentialWorkflow** seçeneğini seçerek sıralı iş akışının etkinlik tabanlı grafik temsilini gösteren **sıralı iş akışı** görünümünü görüntüleyin. Veya **Iş akışı** menüsünden **SequentialWorkflow görüntüle** ' yi seçin.|
|**Iptal Işleyicisini görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünde, iş akışıyla ilişkili [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) etkinliğini gösteren **sıralı iş akışı** görünümünü görüntülemek Için Içerik menüsünden **iptal işleyicisini görüntüle** seçeneğini belirleyin. Veya **Iş akışı** menüsünden **iptal işleyicisini görüntüle** ' yi seçin.|
|**Hata Işleyicisini görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünden **hata Işleyicisini görüntüle** seçeneğini seçerek iş akışıyla Ilişkili [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) etkinliğini gösteren **hatalar** görünümünü görüntüleyin. Veya **Iş akışı** menüsünden **hata işleyicisini görüntüle** ' yi seçin.|

 Benzer görünümler hakkında daha fazla bilgi için bkz. [etkinlik görünümleri (eski)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Etkinlik görünümleri (eski)](../workflow-designer/activity-views-legacy.md) [eski iş akışı projeleri oluşturma](../workflow-designer/creating-legacy-workflow-projects.md) [iş akışı yazma modları](https://msdn2.microsoft.com/library/bb628440.aspx)
