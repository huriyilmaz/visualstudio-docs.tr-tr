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
ms.openlocfilehash: a9848ff2ad312f3dd7d46f4891d9be25add92b0f2f8291beacdbf1050a29d650
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121284210"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı

**TransactedReceiveScope tasarımcısı,** etkinlik oluşturmak ve yapılandırmak için <xref:System.ServiceModel.Activities.TransactedReceiveScope> kullanılır.

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope Etkinliği

Etkinlik, <xref:System.ServiceModel.Activities.TransactedReceiveScope> bir işlemi bir iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemlerine akışınızı sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısını Kullanma

Araç Kutusunun **Mesajlaşma kategorisinde transactedReceiveScope** **etkinlik** **tasarımcısına erişin.** **TransactedReceiveScope** etkinlik **tasarımcısı, etkinlikler** genellikle yerleştirildikten sonra Araç Kutusundan sürükleyip İş Akışı Tasarımcısı yüzeyine bırakılır. Bu, <xref:System.ServiceModel.Activities.TransactedReceiveScope> transactedReceiveScope **varsayılan DisplayName** değerine sahip bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TransactedReceiveScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

**TransactedReceiveScope tasarımcısı** İstek ve **Gövde** **kutularını** içerir. Bunlar, bir etkinliği <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> ve diğer bazı belirten bir özelliği belirten özelliğini yapılandırmak için <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> <xref:System.Activities.Activity> kullanılır. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>bir işlem oluşturur. İşlem daha sonra kapsamı için ortam yapılır, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> böylece bu kapsam içindeki tüm etkinlikler bu işlem içinde yürütülür.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope Özellikleri

Aşağıdaki tablo, <xref:System.ServiceModel.Activities.TransactedReceiveScope> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellik özellik kılavuzunda veya İş Akışı Tasarımcısı düzenlenebilir, ancak diğerleri <xref:System.Activities.Activity.DisplayName%2A> tasarım yüzeyinde düzenlenemez.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.ServiceModel.Activities.TransactedReceiveScope> adı. Varsayılan değer TransactedReceiveScope'tur.<br /><br /> Ad kesinlikle gerekli değildir ancak görünen ad kullanmak <xref:System.Activities.Activity.DisplayName%2A> en iyi yöntemdir.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|Etkinlik tasarımcısı <xref:System.ServiceModel.Activities.Receive> **yüzeyindeki İstek** bloğuna bir etkinlik gösterir.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Yanlış|Etkinlik tasarımcısı <xref:System.Activities.Activity> yüzeyinde **gövde** bloğuna bir atlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)