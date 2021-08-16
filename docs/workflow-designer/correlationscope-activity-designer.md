---
title: İş Akışı Tasarımcısı - CorrelationScope Etkinlik Tasarımcısı
description: CorrelationScope etkinlik tasarımcısını kullanarak correlationScope etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b958aa6568461ac9e753bfa8a0e304b3cabaf4e3687e648a9fc9853d113fe51a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383917"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope Etkinlik Tasarımcısı

**CorrelationScope** etkinlik tasarımcısı, bir nesnesi kullanarak alt mesajlaşma etkinliklerinin örtülü yönetimini sağlayan bir etkinlik <xref:System.ServiceModel.Activities.CorrelationScope> oluşturmak ve yapılandırmak için <xref:System.ServiceModel.Activities.CorrelationHandle> kullanılır.

## <a name="the-correlationscope-activity"></a>CorrelationScope etkinliği

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>özelliği, alt mesajlaşma <xref:System.ServiceModel.Activities.CorrelationHandle> etkinliklerini yönetmek için kullanılanı belirtir. içinde <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> yer alan ve <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> etkinlikleri, bağıntı gerçekleştirmek için <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> içeren etkinliğin <xref:System.ServiceModel.Activities.CorrelationScope> özelliğini kullanmak üzere yapılandırılır.

### <a name="use-the-correlationscope-activity-designer"></a>CorrelationScope Etkinlik Tasarımcısını Kullanma

**CorrelationScope** etkinlik tasarımcısı, araç kutusunun sol tarafındaki Araç Kutusu sekmesine tıklayarak  erişilen Mesajlaşma kategorisinde İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**CorrelationScope** etkinlik tasarımcısı Araç Kutusundan **sürüklenip** İş Akışı Tasarımcısı bırakılır. Bu, varsayılan <xref:System.ServiceModel.Activities.CorrelationScope> CorrelationScope **DisplayName değerine sahip** bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **CorrelationScope** etkinlik tasarımcısının üst bilgisinde veya Özellikler penceresinin **DisplayName** kutusunda **düzenlenebilir.**

Alt mesajlaşma etkinlikleri tarafından kullanılan öğesini belirtmek <xref:System.ServiceModel.Activities.CorrelationHandle> için Özellikler **penceresindeki CorrelatesWith**  alanı yanındaki üç nokta düğmesini seçerek İfade Düzenleyicisi **iletişim** kutusunu açın. Bu özellik etkinlik tasarımcısı yüzeyinde de ayarlandırabilirsiniz.

Bağıntı kapsamındaki etkinlikler, **correlationScope** tasarımcısı içindeki **Gövde** kutusuna tasarımcıları bırakarak belirtilir.

### <a name="the-correlationscope-properties"></a>CorrelationScope özellikleri

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.CorrelationScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler Özellikler penceresinde veya **İş Akışı Tasarımcısı** hem de her ikisinde de düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.ServiceModel.Activities.InitializeCorrelation> adı.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Yanlış|Alt mesajlaşma <xref:System.ServiceModel.Activities.CorrelationHandle> etkinliklerini yönetmek için kullanılanı belirtir. Bu özelliği ayarlasanız otomatik <xref:System.ServiceModel.Activities.CorrelationScope> olarak bir örtülü <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Yanlış|Bağıntı kapsamındaki etkinlikleri belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)