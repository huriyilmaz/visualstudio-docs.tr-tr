---
title: İş Akışı Tasarımcısı-SendAndReceiveReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17512337b58fb394352ccaab153ca72badbb4652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875910"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı

**SendAndReceiveReply** şablonu, önceden yapılandırılmış ve etkinlik çifti oluşturmak için kullanılır <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Etkinlikler bir <xref:System.Activities.Statements.Sequence> etkinliğin parçasıdır ve istemcideki istek/yanıt iletisi değişim deseninin bir parçası olarak bağıntılı.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu

**SendAndReceiveReply** şablonunu eklemek, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> bir etkinlik içinde ve etkinliklerini oluşturmanın yanı sıra üç şeyi de yapar <xref:System.Activities.Statements.Sequence> :

- <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> Etkinliğin ve özelliklerini yapılandırır <xref:System.ServiceModel.Activities.Send> .

- <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> <xref:System.ServiceModel.Activities.ReceiveReply> Etkinliğin özelliğini etkinliğe bağlar <xref:System.ServiceModel.Activities.Send> .

- <xref:System.ServiceModel.Activities.CorrelationHandle>Üst etkinlikte bir değişken olarak oluşturur.

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **SendAndReceiveReply** etkinlik tasarımcısına erişin. **SendAndReceiveReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısının atılması, <xref:System.ServiceModel.Activities.Send> **Send** Activity Designer ile yapılandırılabilen bir etkinlik ve <xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend** Tasarımcısı ile yapılandırılabilecek bir bağıntılı oluşturur.

Etkinliği yapılandırmak için **gönderme** tasarımcısını kullanma hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Send> bkz. [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Yanlış | Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.ReceiveReply> . Varsayılan değer ReceiveReplyForSend ' dir.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Doğru | <xref:System.ServiceModel.Activities.Send>Bu etkinlikle eşleştirilmiş etkinliğe başvuru <xref:System.ServiceModel.Activities.ReceiveReply> . Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri, istemci üzerinde bir istek/yanıt mesajlaşma modelini modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmek gerektiğini belirtir. Tasarımcıda Bu özelliği düzenleyemezsiniz, çünkü <xref:System.ServiceModel.Activities.Send> etkinliği oluşturduğunuz etkinliğe otomatik olarak bağlanır <xref:System.ServiceModel.Activities.ReceiveReply> . |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Yanlış | Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki üç nokta düğmesine tıklayarak veya **alma** etkinliği Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki **Tanımla** düğmesine tıklayarak bu özelliği düzenleyin. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Yanlış | <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Yanlış | İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)