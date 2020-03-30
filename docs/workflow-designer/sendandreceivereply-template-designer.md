---
title: İş Akışı Tasarımcısı - SendAndReceiveReply Şablon Tasarımcısı
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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395240"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı

**SendAndReceiveReply** şablonu, önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bir dizi etkinlik oluşturmak için kullanılır. Etkinlikler bir etkinliğin <xref:System.Activities.Statements.Sequence> parçasıdır ve istemcideki istek/yanıt iletisi değiştirme deseninin bir parçası olarak ilişkilidir.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu

**SendAndReceiveReply** şablonu ekleme, bir <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.Sequence> etkinlik içinde ve etkinlikleri oluşturmanın yanı sıra üç şey yapar:

- Etkinliğin <xref:System.ServiceModel.Activities.Send.OperationName%2A> özelliklerini <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> ve özelliklerini yapılandırır. <xref:System.ServiceModel.Activities.Send>

- Etkinliğin <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> aktiviteye bağlar.

- Üst etkinlikte <xref:System.ServiceModel.Activities.CorrelationHandle> değişken olarak bir değişken oluşturur.

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply ŞablonU Tasarımcısını Kullanın

**Toolbox'ın** **Mesajlaşma** kategorisinde **SendAndReceiveReply** etkinlik tasarımcısına erişin. **SendAndReceiveReply** etkinlik tasarımcısı **Araç Kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde İş Akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik tasarımcısıbırakarak, <xref:System.ServiceModel.Activities.Send> **Gönder** etkinliği tasarımcısı yla yapılandırılabilen bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik ve **ReceiveReplyForSend** tasarımcısıyla yapılandırılabilen bir ilişkili etkinlik oluşturur.

Etkinliği yapılandırmak için **Gönder** tasarımcısını <xref:System.ServiceModel.Activities.Send> kullanma hakkında daha fazla bilgi için bkz. [Send](../workflow-designer/send-activity-designer.md)

### <a name="properties-of-receivereply"></a>ReceiveReply'In Özellikleri

Aşağıdaki tablo özellikleri <xref:System.ServiceModel.Activities.ReceiveReply> gösterir ve tasarımcınasıl kullanıldığını açıklar. Bu özellikler özellikler ızgarasında düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilir.

| Özellik Adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.ReceiveReply> Etkinliğin isteğe bağlı dostu adı. Varsayılan receiveReplyForSend olduğunu.<br /><br /> Dost <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değerin kullanılması kesinlikle gerekli olmasa da, böyle bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Bu <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikle eşleştirilmiş aktiviteye başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send>ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler bir istek/yanıt iletisi deseni modellemek için istemci üzerinde birlikte kullanılır. Bu özellik, hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşlenere olduğunu belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği oluşturduğunuz faaliyete otomatik olarak bağlı olduğundan bu özelliği ayarlayamazsınız. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Alınacak ileti veya parametre içeriğini belirtir. Bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik **ızgarasındaki İçerik** alanının yanındaki elips düğmesini tıklatarak veya **Etkinlik** tasarımcısı yüzeyinde **İçerik** etiketinin yanındaki **Tanımla** düğmesini tıklatarak bu özelliği düzenleme. Her ikisi de **İçerik Tanımı** iletişim kutusunu görüntüler. Bu kutunun nasıl kullanılacağı hakkında daha fazla bilgi için [İçerik Tanımı İletişim Kutusu'na](../workflow-designer/content-definition-dialog-box.md)bakın. |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | İş akışı içinde <xref:System.ServiceModel.Activities.CorrelationInitializer> bu <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> etkinliği yapılandıran birden çok nesneyi açan nesnelerin toplanmasını belirtir. <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **Bağıntı Ekle Initializers** iletişim kutusunu açmak için özellikler ızgarasında ki özelliğin yanındaki elips düğmesini tıklatın. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz: [Bağıntı EkleInitializers İletişim Kutusu.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)