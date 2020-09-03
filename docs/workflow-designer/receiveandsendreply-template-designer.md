---
title: İş Akışı Tasarımcısı-ReceiveAndSendReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66822664766ac64e466882fda27906f56ebb4aad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876014"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı

**ReceiveAndSendReply** şablonu, önceden yapılandırılmış ve etkinlik çifti oluşturmak için kullanılır <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Etkinlikler bir <xref:System.Activities.Statements.Sequence> etkinliğin parçasıdır ve sunucudaki bir istek/yanıt iletisi değişim deseninin parçası olarak bağıntılı bir belgedir.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu

Bir **ReceiveAndSendReply** şablonu eklemek, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerini bir etkinlik ile oluşturmanın yanı sıra üç şeyi de yapar <xref:System.Activities.Statements.Sequence> :

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> Etkinliğin ve özelliklerini yapılandırır <xref:System.ServiceModel.Activities.Receive> .

- <xref:System.ServiceModel.Activities.SendReply.Request%2A> <xref:System.ServiceModel.Activities.Receive> Etkinliğin özelliğini etkinliğe bağlar <xref:System.ServiceModel.Activities.Send> .

- <xref:System.ServiceModel.Activities.CorrelationHandle>Üst etkinlikte bir değişken olarak oluşturur.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **ReceiveAndSendReply** etkinlik tasarımcısına erişin. **ReceiveAndSendReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısının atılması, <xref:System.ServiceModel.Activities.Receive> **Send** Activity Designer ile yapılandırılabilen bir etkinlik ve <xref:System.ServiceModel.Activities.SendReply> SendReplyToReceive Tasarımcısı ile yapılandırılabilecek bir bağıntılı oluşturur.

Etkinliği yapılandırmak için **alma** tasarımcısını kullanma hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Receive> bkz. [etkinlik tasarımcısını alma](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>SendReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.SendReply> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler Özellikler kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.SendReply> . Varsayılan değer SendReplyToReceive ' dir.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Doğru | <xref:System.ServiceModel.Activities.Receive>Bu etkinlikle eşleştirilmiş etkinliğe başvuru <xref:System.ServiceModel.Activities.SendReply> . Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, istek/yanıt mesajlaşma modelini modellemek için sunucuda birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmek gerektiğini belirtir. Tasarımcıda Bu özelliği düzenleyemezsiniz, çünkü <xref:System.ServiceModel.Activities.Send> etkinliği oluşturduğunuz etkinliğe otomatik olarak bağlanır <xref:System.ServiceModel.Activities.SendReply> . |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Yanlış | Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesine tıklayarak veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **Tanımla** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusu. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Yanlış | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Yanlış | Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olup olmayacağını belirtir. Varsayılan değer **false** şeklindedir. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)