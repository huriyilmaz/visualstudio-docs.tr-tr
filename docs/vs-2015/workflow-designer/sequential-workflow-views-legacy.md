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
ms.openlocfilehash: 8acc9bfcac476425ac6c6b967b1a3b3a34310d8a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663220"
---
# <a name="sequential-workflow-views-legacy"></a>Sıralı İş Akışı Görünümleri (Eski)
[!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemek için kullanılabilecek eski bir [!INCLUDE[wfd1](../includes/wfd1-md.md)] sağlar.

 @No__t_0 tanıdık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabirimini kullanarak [!INCLUDE[wf](../includes/wf-md.md)] uygulamaları grafiksel olarak oluşturmak için bir yol sağlar. [!INCLUDE[wf](../includes/wf-md.md)] uygulamalar, etkinlik olarak adlandırılan iş akışı işlemi adımlarından oluşur. Bir iş akışı oluşturmak için, ilgili etkinlik tasarımcılarını **araç kutusu** 'ndan tasarım yüzeyine sürükleyerek tasarım yüzeyine etkinlik oluşturun.

 Bir [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)olan sıralı bir iş akışı oluşturduğunuzda, iş akışının üç görünümü kullanılabilir. Bu görünümlere, **Iş akışı** menüsünden ve tasarım yüzeyindeki bağlam menüsünden erişilebilir.

 Aşağıdaki tabloda her bir görünümün adı ve açıklaması listelenmektedir.

|Menü/sekme seçeneği|Açıklama|
|----------------------|-----------------|
|**SequentialWorkflow görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünde **Görünüm SequentialWorkflow** seçeneğini seçerek sıralı iş akışının etkinlik tabanlı grafik temsilini gösteren **sıralı iş akışı** görünümünü görüntüleyin. Veya **Iş akışı** menüsünden **SequentialWorkflow görüntüle** ' yi seçin.|
|**Iptal Işleyicisini görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünde, iş akışıyla ilişkili [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) etkinliğini gösteren **sıralı iş akışı** görünümünü görüntülemek Için Içerik menüsünden **iptal işleyicisini görüntüle** seçeneğini belirleyin. Veya **Iş akışı** menüsünden **iptal işleyicisini görüntüle** ' yi seçin.|
|**Hata Işleyicisini görüntüle**|Tasarım yüzeyine sağ tıklayın ve bağlam menüsünden **hata Işleyicisini görüntüle** seçeneğini seçerek iş akışıyla Ilişkili [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) etkinliğini gösteren **hatalar** görünümünü görüntüleyin. Veya **Iş akışı** menüsünden **hata işleyicisini görüntüle** ' yi seçin.|

 Benzer görünümler hakkında daha fazla bilgi için bkz. [etkinlik görünümleri (eski)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Etkinlik görünümleri (eski)](../workflow-designer/activity-views-legacy.md) [eski iş akışı projeleri oluşturma](../workflow-designer/creating-legacy-workflow-projects.md) [iş akışı yazma modları](http://go.microsoft.com/fwlink?LinkID=65014)