---
title: SendAndReceiveReply Şablon Tasarımcısı | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395338"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı
**SendAndReceiveReply** şablonu, istemcideki istek/yanıt iletisi değiştirme <xref:System.Activities.Statements.Sequence> deseninin bir parçası olarak ilişkili bir etkinlik içinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik içeren bir çift etkinlik oluşturmak için kullanılır.

## <a name="the-sendandreceivereply-template"></a>SendandReceiveYanıt Şablonu
 **SendAndReceiveReply** şablonu ekleme bir <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.Sequence> etkinlik içinde ve faaliyetleri oluşturmanın yanı sıra üç şey yapar:

1. Etkinliğin <xref:System.ServiceModel.Activities.Send.OperationName%2A>özelliklerini <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> yapılandırır. <xref:System.ServiceModel.Activities.Send>

2. Etkinliğin <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> aktiviteye bağlar.

3. Üst etkinlikte <xref:System.ServiceModel.Activities.CorrelationHandle> değişken olarak bir değişken oluşturur.

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısını Kullanma
 **SendAndReceiveReply** etkinlik tasarımcısı, **Araç Kutusu'nun** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Mesajlaşma** kategorisinde bulunabilir ( Alternatif olarak, **Görünüm** menüsünden **Araç Çubuğu'nu** veya CTRL+ALT+X'i seçin.) **Toolbox**

 **SendAndReceiveReply** etkinlik tasarımcısı **Araç Kutusundan** sürüklenebilir ve etkinliklerin [!INCLUDE[wfd2](../includes/wfd2-md.md)] genellikle yerleştirildiği her yerde yüzeye bırakılabilir. Bu, Gönder <xref:System.ServiceModel.Activities.Send> etkinliği tasarımcısı yla yapılandırılabilen bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik ve **ReceiveReplyForSend** tasarımcısıyla yapılandırılabilen bir ilişkili etkinlik oluşturur. **Send**

 [!INCLUDE[crabout](../includes/crabout-md.md)]etkinliği **Send** yapılandırmak için Gönder <xref:System.ServiceModel.Activities.Send> tasarımcısını kullanarak [Gönder](../workflow-designer/send-activity-designer.md) konusuna bakın.

 [!INCLUDE[crabout](../includes/crabout-md.md)]etkinliği yapılandırmak için **ReceiveReplyForSend** tasarımcısını <xref:System.ServiceModel.Activities.ReceiveReply> kullanarak aşağıdaki bölüme bakın.

### <a name="properties-of-receivereply"></a>ReceiveReply'In Özellikleri
 Aşağıdaki tablo <xref:System.ServiceModel.Activities.ReceiveReply> özellikleri gösterir ve tasarımcınasıl kullanıldığını açıklar. Bu özellikler özellikleri ızgara düzenlenebilir ve bazı [!INCLUDE[wfd2](../includes/wfd2-md.md)]tasarımcı yüzeyinde düzenlenebilir.

|                                 Özellik Adı                                 | Gerekli |                                                                                                                                                                                                                                                                                                                                                        Kullanım                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.ReceiveReply> Etkinliğin isteğe bağlı dostu adı. Varsayılan receiveReplyForSend olduğunu.<br /><br /> Dost <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değerin kullanılması kesinlikle gerekli olmasa da, böyle bir değeri kullanmak en iyi yöntemdir.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Bu <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikle eşleştirilmiş aktiviteye başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send>ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler bir istek/yanıt iletisi deseni modellemek için istemci üzerinde birlikte kullanılır. Bu özellik, hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşlenere olduğunu belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği oluşturduğunuz faaliyete otomatik olarak bağlı olduğundan bu özelliği kaldıramazsınız. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Alınacak ileti veya parametre içeriğini belirtir. Bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik ızgarasında **İçerik** alanının yanındaki elips düğmesini tıklatarak veya **Tanımla'yı** tıklatarak bu özelliği düzenleme... **etkinlik** tasarımcısı **yüzeyindeİçerik** etiketinin yanındaki düğmeyi. Her ikisi de **İçerik Tanımı** iletişim kutusunu görüntüler. [!INCLUDE[crabout](../includes/crabout-md.md)]bu kutuyu nasıl kullanacağınız, [İçerik Tanımı İletişim Kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              İş akışı içinde <xref:System.ServiceModel.Activities.CorrelationInitializer> bu <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> etkinliği yapılandıran birden çok nesneyi açan nesnelerin toplanmasını belirtir. <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **Bağıntı Ekle Initializers** iletişim kutusunu açmak için özellikler ızgarasında ki özelliğin yanındaki elips düğmesini tıklatın. [!INCLUDE[crabout](../includes/crabout-md.md)]bu kutuyu [kullanarak, Bağıntı EkleInitializers İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [Gönder TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)