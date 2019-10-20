---
title: İş Akışı Tasarımcısı-ReceiveAndSendReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650031"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı

**ReceiveAndSendReply** şablonu, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerinin çiftini oluşturmak için kullanılır. Etkinlikler <xref:System.Activities.Statements.Sequence> etkinliğin bir parçasıdır ve sunucudaki istek/yanıt iletisi değişim deseninin bir parçası olarak bağıntılı bir belgedir.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu

Bir **ReceiveAndSendReply** şablonu eklemek, bir <xref:System.Activities.Statements.Sequence> etkinliğiyle <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerini oluşturmanın yanı sıra üç şey yapar:

- @No__t_2 etkinliğinin <xref:System.ServiceModel.Activities.Receive.OperationName%2A> ve <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> özelliklerini yapılandırır.

- @No__t_1 etkinliğinin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Send> etkinliğine bağlar.

- Üst etkinlikte değişken olarak bir <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **ReceiveAndSendReply** etkinlik tasarımcısına erişin. **ReceiveAndSendReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısının atılması, **gönderme** etkinliği Tasarımcısı ile yapılandırılabilen bir <xref:System.ServiceModel.Activities.Receive> etkinlik ve SendReplyToReceive Tasarımcısı ile yapılandırılabilen bağıntılı bir <xref:System.ServiceModel.Activities.SendReply> oluşturur.

@No__t_1 etkinliğini yapılandırmak için **alma** tasarımcısını kullanma hakkında daha fazla bilgi için bkz. [etkinlik tasarımcısını alma](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>SendReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.SendReply> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler Özellikler kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | @No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer SendReplyToReceive ' dir.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Doğru | Bu <xref:System.ServiceModel.Activities.SendReply> etkinliğiyle eşleştirilmiş <xref:System.ServiceModel.Activities.Receive> etkinliğine başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, sunucu üzerinde bir istek/yanıt mesajlaşma modeli modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğinin eşleştirilmek gerektiğini belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.SendReply> etkinliğini oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğe otomatik olarak bağlandığından bu özelliği düzenleyemezsiniz. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Alacak ileti veya parametre içeriğini belirtir. @No__t_0 bir etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliği olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesine tıklayarak veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **Tanımla** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Bu <xref:System.ServiceModel.Activities.Receive> etkinliğini iş akışı içinde yapılandıran birden çok <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesini başlatacak <xref:System.ServiceModel.Activities.CorrelationInitializer> nesnelerinin koleksiyonunu belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusu. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> <strong>https://tempuri.org/{service sözleşme ad alanı}/{Service sözleşme adı}/{Operation Name}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olup olmayacağını belirtir. Varsayılan değer **false**'dur. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)