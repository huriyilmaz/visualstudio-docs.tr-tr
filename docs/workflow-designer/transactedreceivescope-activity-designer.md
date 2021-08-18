---
title: TransactedReceiveScope etkinlik tasarımcısı
description: Bu İş Akışı Tasarımcısı TransactedReceiveScope tasarımcısını kullanarak TransactedReceiveScope etkinliği oluşturma ve yapılandırma hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: cbdbd2ce46e5d9d6bf9f0f69c81c9bfdaa0b1d6d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135123"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı

**TransactedReceiveScope tasarımcısı,** etkinlik oluşturmak ve yapılandırmak için <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullanılır.

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope Etkinliği

Etkinlik, <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir işlemi bir iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemlerine akışınızı sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısını Kullanma

Araç Kutusunun **Mesajlaşma kategorisinde transactedReceiveScope** **etkinlik** **tasarımcısına erişin.** **TransactedReceiveScope** etkinlik **tasarımcısı, etkinlikler** genellikle yerleştirildikten sonra Araç Kutusundan İş Akışı Tasarımcısı yüzeyine sürüklenir. Bu, <xref:System.ServiceModel.Activities.TransactedReceiveScope> transactedReceiveScope **varsayılan DisplayName** değerine sahip bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TransactedReceiveScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

**TransactedReceiveScope tasarımcısı** İstek ve **Gövde** **kutularını** içerir. Bunlar, bir etkinliği <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> ve diğer bazı belirten bir özelliği belirten özelliğini yapılandırmak için <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> <xref:System.Activities.Activity> kullanılır. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>bir işlem oluşturur. İşlem daha sonra kapsamı için ortam yapılır, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> böylece bu kapsam içindeki tüm etkinlikler bu işlem içinde yürütülür.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope Özellikleri

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.TransactedReceiveScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellik özellik kılavuzunda veya İş Akışı Tasarımcısı <xref:System.Activities.Activity.DisplayName%2A> düzenlenebilir, ancak diğerleri tasarım yüzeyinde düzenlenemez.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.ServiceModel.Activities.TransactedReceiveScope> adı. Varsayılan değer TransactedReceiveScope'tur.<br /><br /> Ad <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|Etkinlik <xref:System.ServiceModel.Activities.Receive> tasarımcısının **yüzeyindeki** İstek bloğuna bir etkinlik gösterir.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Yanlış|Etkinlik tasarımcısı <xref:System.Activities.Activity> yüzeyinde **gövde** bloğuna bir atlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)