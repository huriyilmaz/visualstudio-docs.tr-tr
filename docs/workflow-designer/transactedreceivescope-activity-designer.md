---
title: İş Akışı Tasarımcısı-TransactedReceiveScope etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf5a52a6a806d72632bf31a7c73e41677e9ddaf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654287"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı

**TransactedReceiveScope** Tasarımcısı, bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope etkinliği

@No__t_0 etkinliği bir işlem, bir iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemlerine akabilmenizi sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **TransactedReceiveScope** etkinlik tasarımcısına erişin. **TransactedReceiveScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu, TransactedReceiveScope 'un varsayılan **DisplayName** 'i olan bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği oluşturur. @No__t_0, **TransactedReceiveScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

**TransactedReceiveScope** Tasarımcısı **istek** ve **gövde** kutularını içerir. Bunlar, bir <xref:System.ServiceModel.Activities.Receive> etkinliği ve diğer <xref:System.Activities.Activity> belirten bir <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> özelliğini belirten <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> özelliğini yapılandırmak için kullanılır. @No__t_0 bir işlem oluşturur. Daha sonra işlem, bu kapsamdaki herhangi bir etkinliğin bu işlem içinde yürütüldüğü şekilde <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> kapsamı için çevresel hale getirilir.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.TransactedReceiveScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu <xref:System.Activities.Activity.DisplayName%2A> özelliği özellik kılavuzunda veya İş Akışı Tasarımcısı yüzeyinde düzenlenebilir, ancak diğerleri tasarım yüzeyinde düzenlenmelidir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer TransactedReceiveScope ' dir.<br /><br /> @No__t_0 adı kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|Etkinlik Tasarımcısı yüzeyinde bir <xref:System.ServiceModel.Activities.Receive> etkinliğini **istek** bloğuna bırakır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Etkinlik Tasarımcısı yüzeyinde bir <xref:System.Activities.Activity> **gövde** bloğuna bırakır.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)