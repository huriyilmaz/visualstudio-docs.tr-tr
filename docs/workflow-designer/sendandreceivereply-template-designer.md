---
title: İş Akışı Tasarımcısı-SendAndReceiveReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649965"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı

**SendAndReceiveReply** şablonu, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerin çiftini oluşturmak için kullanılır. Etkinlikler <xref:System.Activities.Statements.Sequence> etkinliğin bir parçasıdır ve istemcideki istek/yanıt iletisi değişim deseninin bir parçası olarak bağıntılı bir belgedir.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu

**SendAndReceiveReply** şablonunu eklemek, bir <xref:System.Activities.Statements.Sequence> etkinliğinde <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerini oluşturmanın yanı sıra üç şey yapar:

- @No__t_2 etkinliğinin <xref:System.ServiceModel.Activities.Send.OperationName%2A> ve <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> özelliklerini yapılandırır.

- @No__t_1 etkinliğinin <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Send> etkinliğine bağlar.

- Üst etkinlikte değişken olarak bir <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **SendAndReceiveReply** etkinlik tasarımcısına erişin. **SendAndReceiveReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısının atılması, **Send** Activity Designer ile yapılandırılabilen bir <xref:System.ServiceModel.Activities.Send> etkinlik ve **ReceiveReplyForSend** Tasarımcısı ile yapılandırılabilecek bir bağıntılı <xref:System.ServiceModel.Activities.ReceiveReply> oluşturur.

@No__t_1 etkinliğini yapılandırmak için **gönderme** tasarımcısını kullanma hakkında daha fazla bilgi için bkz. [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | @No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer ReceiveReplyForSend ' dir.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Doğru | Bu <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğiyle eşleştirilmiş <xref:System.ServiceModel.Activities.Send> etkinliğine başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri, istemci üzerinde bir istek/yanıt mesajlaşma modelini modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğinin eşleştirilmek gerektiğini belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğe otomatik olarak bağlandığından bu özelliği düzenleyemezsiniz. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Alacak ileti veya parametre içeriğini belirtir. @No__t_0 bir etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliği olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesine tıklayarak veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **Tanımla** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Bu <xref:System.ServiceModel.Activities.Receive> etkinliğini iş akışı içinde yapılandıran birden çok <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesini başlatacak <xref:System.ServiceModel.Activities.CorrelationInitializer> nesnelerinin koleksiyonunu belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> <strong>https://tempuri.org/{service sözleşme ad alanı}/{Service sözleşme adı}/{Operation Name}.</strong> |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)