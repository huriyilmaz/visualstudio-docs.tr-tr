---
title: İş Akışı Tasarımcısı-CorrelationScope etkinlik Tasarımcısı
description: CorrelationScope etkinliği oluşturmak ve yapılandırmak için CorrelationScope etkinlik Tasarımcısı 'nı nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9edd755465cf812c1572c62f1c6335fc5295281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955533"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope Etkinlik Tasarımcısı

**CorrelationScope** etkinlik Tasarımcısı, <xref:System.ServiceModel.Activities.CorrelationScope> bir nesne kullanarak alt mesajlaşma etkinliklerinin örtük yönetimi sağlayan bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.CorrelationHandle> .

## <a name="the-correlationscope-activity"></a>CorrelationScope etkinliği

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>Özelliği, <xref:System.ServiceModel.Activities.CorrelationHandle> alt ileti etkinliklerini yönetmek için kullanılan öğesini belirtir. <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> İçinde bulunan ve etkinlikleri, <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> bağıntı gerçekleştirmek için kapsayan etkinliğin özelliğini kullanmak üzere yapılandırılmıştır <xref:System.ServiceModel.Activities.CorrelationScope> .

### <a name="use-the-correlationscope-activity-designer"></a>CorrelationScope etkinlik tasarımcısını kullanma

**CorrelationScope** etkinlik tasarımcısı, iş akışı Tasarımcısı sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **mesajlaşma** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

**CorrelationScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.CorrelationScope> , varsayılan olarak bir CorrelationScope **DisplayName** 'i olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **CorrelationScope** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

<xref:System.ServiceModel.Activities.CorrelationHandle>Alt mesajlaşma etkinlikleri tarafından kullanılan öğesini belirtmek için, **Özellikler** penceresinde **CorrelatesWith** alanının yanındaki üç nokta düğmesini seçerek **ifade Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu özellik, etkinlik Tasarımcısı yüzeyi üzerinde de ayarlanabilir.

Bağıntı dahilinde olan etkinlikler, kendi tasarımcıların, **CorrelationScope** Designer içindeki **gövde** kutusu içine bırakılarak belirlenir.

### <a name="the-correlationscope-properties"></a>CorrelationScope özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.CorrelationScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya iş akışı Tasarımcısı yüzeyinde ve genellikle her ikisinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Yanlış|<xref:System.ServiceModel.Activities.CorrelationHandle>Alt ileti etkinliklerini yönetmek için kullanılan öğesini belirtir. Bu özelliği ayarlanmamışsa, <xref:System.ServiceModel.Activities.CorrelationScope> <xref:System.ServiceModel.Activities.CorrelationHandle> otomatik olarak örtülü olarak oluşturulur.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Yanlış|Bağıntı kapsamındaki etkinlikleri belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)