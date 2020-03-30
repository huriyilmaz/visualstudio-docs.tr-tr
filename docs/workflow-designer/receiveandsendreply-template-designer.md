---
title: İş Akışı Tasarımcısı - ReceiveAndSendReply Şablon Tasarımcısı
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
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395294"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı

**ReceiveAndSendReply** şablonu, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri oluşturmak için kullanılır. Etkinlikler bir <xref:System.Activities.Statements.Sequence> etkinliğin parçasıdır ve sunucudaki istek/yanıt iletisi değiştirme deseninin bir parçası olarak ilişkilidir.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu

**ReceiveAndSendReply** şablonu eklemek, bir <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> etkinlikle ve etkinlikleri oluşturmanın yanı sıra üç şey yapar:

- Etkinliğin <xref:System.ServiceModel.Activities.Receive.OperationName%2A> özelliklerini <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> ve özelliklerini yapılandırır. <xref:System.ServiceModel.Activities.Receive>

- Etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> aktiviteye bağlar.

- Üst etkinlikte <xref:System.ServiceModel.Activities.CorrelationHandle> değişken olarak bir değişken oluşturur.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply şablonu tasarımcısını kullanma

**Toolbox'ın** **Mesajlaşma** **kategorisindereceiveAndSendReply** etkinlik tasarımcısına erişin. **ReceiveAndSendReply** etkinlik tasarımcısı **Araç Kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde İş Akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısıbırakarak, <xref:System.ServiceModel.Activities.Receive> **Gönder** etkinliği tasarımcısı yla yapılandırılabilen bir <xref:System.ServiceModel.Activities.SendReply> etkinlik ve SendReplyToReceive tasarımcısıyla yapılandırılabilen bir ilişkili etkinlik oluşturur.

Etkinliği yapılandırmak için **Al** tasarımcısını <xref:System.ServiceModel.Activities.Receive> kullanma hakkında daha fazla bilgi için bkz. [Receive Activity Designer](../workflow-designer/receive-activity-designer.md)

### <a name="properties-of-sendreply"></a>SendReply özellikleri

Aşağıdaki tablo <xref:System.ServiceModel.Activities.SendReply> özellikleri gösterir ve tasarımcınasıl kullanıldığını açıklar. Bu özellikler özellikler ızgarasında düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> Etkinliğin isteğe bağlı dostu adı. Varsayılan sendReplyToReceive olduğunu.<br /><br /> Dost <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değerin kullanılması kesinlikle gerekli olmasa da, böyle bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Bu <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> etkinlikle eşleştirilmiş aktiviteye başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler bir istek/yanıt iletisi deseni modellemek için sunucuda birlikte kullanılır. Bu özellik, hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşlenere olduğunu belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> etkinliği oluşturduğunuz faaliyete otomatik olarak bağlı olduğundan bu özelliği ayarlayamazsınız. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Alınacak ileti veya parametre içeriğini belirtir. Bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik **ızgarasındaki İçerik** alanının yanındaki elips düğmesini tıklatarak veya **Etkinlik** tasarımcısı yüzeyinde **İçerik** etiketinin yanındaki **Tanımla** düğmesini tıklatarak bu özelliği düzenleme. Her ikisi de **İçerik Tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [İçerik Tanımı İletişim Kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | İş akışı içinde <xref:System.ServiceModel.Activities.CorrelationInitializer> bu <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> etkinliği yapılandıran birden çok nesneyi açan nesnelerin toplanmasını belirtir. <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> **Bağıntı Ekle Initializers** iletişim kutusunu açmak için özellikler ızgarasında ki özelliğin yanındaki elips düğmesini tıklatın. Bu kutuyu kullanma hakkında daha fazla bilgi [için, Bağıntı EkleInitializers İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olarak devam edip etmeyeceğini belirtir. Varsayılan değer **false** şeklindedir. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)