---
title: TransactedReceiveScope etkinlik Tasarımcısı
description: İş Akışı Tasarımcısı, TransactedReceiveScope tasarımcısını kullanarak bir TransactedReceiveScope etkinliği oluşturma ve yapılandırma hakkında bilgi edinin.
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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963706"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı

**TransactedReceiveScope** Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope etkinliği

<xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, bir işlemi iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemlerine akabilmenizi sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **TransactedReceiveScope** etkinlik tasarımcısına erişin. **TransactedReceiveScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.TransactedReceiveScope> , TransactedReceiveScope 'un varsayılan **DisplayName** 'i olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TransactedReceiveScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

**TransactedReceiveScope** Tasarımcısı **istek** ve **gövde** kutularını içerir. Bunlar <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> , bir <xref:System.ServiceModel.Activities.Receive> etkinliği ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> diğerini belirten özelliği belirleyen özelliği yapılandırmak için kullanılır <xref:System.Activities.Activity> . , <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Bir işlem oluşturur. Daha sonra işlem, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> Bu kapsamdaki herhangi bir etkinliğin bu işlem içinde yürütüldüğü şekilde öğesinin kapsamı için çevresel hale getirilir.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.TransactedReceiveScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu <xref:System.Activities.Activity.DisplayName%2A> özellik, özellik kılavuzunda veya iş akışı Tasarımcısı yüzeyinde düzenlenebilir, ancak diğerleri tasarım yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Varsayılan değer TransactedReceiveScope ' dir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|<xref:System.ServiceModel.Activities.Receive>Etkinlik Tasarımcısı yüzeyinde bir etkinliği **istek** bloğuna bırakır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Yanlış|<xref:System.Activities.Activity>Etkinlik Tasarımcısı yüzeyinde **gövde** bloğunun içine bırakır.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)