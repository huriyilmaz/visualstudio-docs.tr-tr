---
title: ReceiveandSendReply Şablon Tasarımcısı | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395387"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı
**ReceiveAndSendReply** şablonu, sunucudaki istek/yanıt iletisi değiştirme <xref:System.Activities.Statements.Sequence> deseninin bir parçası olarak ilişkili bir etkinlik içinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlik içeren bir çift etkinlik oluşturmak için kullanılır.

## <a name="the-receiveandsendreply-template"></a>ReceiveandSendReply şablonu
 **ReceiveAndSendReply** şablonu ekleme bir <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> etkinlik ile ve faaliyetleri oluşturmanın yanı sıra üç şey yapar:

1. Etkinliğin <xref:System.ServiceModel.Activities.Receive.OperationName%2A>özelliklerini <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> yapılandırır. <xref:System.ServiceModel.Activities.Receive>

2. Etkinliğin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> aktiviteye bağlar.

3. Üst etkinlikte <xref:System.ServiceModel.Activities.CorrelationHandle> değişken olarak bir değişken oluşturur.

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Uyrcadını Kullanma
 **ReceiveAndSendReply** etkinlik tasarımcısı, Araç **Messaging** Kutusu sekmesine tıklayarak erişilen Araç **Kutusu'nun** Mesajlaşma [!INCLUDE[wfd2](../includes/wfd2-md.md)] kategorisinde bulunabilir (Alternatif olarak, **Görünüm** menüsünden **Araç Çubuğu'nu** veya CTRL+ALT+X'i seçin.) **Toolbox**

 **ReceiveAndSendReply** etkinlik tasarımcısı **Araç Kutusundan** sürüklenebilir ve etkinliklerin [!INCLUDE[wfd2](../includes/wfd2-md.md)] genellikle yerleştirildiği her yerde yüzeye bırakılabilir. Bu, **Gönder** etkinliği tasarımcısı yla yapılandırılabilen bir <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> etkinlik ve SendReplyToReceive tasarımcısıyla yapılandırılabilen bir ilişkili etkinlik oluşturur.

 [!INCLUDE[crabout](../includes/crabout-md.md)]etkinliği **Receive** yapılandırmak için Al <xref:System.ServiceModel.Activities.Receive> tasarımcısını [kullanarak, Al](../workflow-designer/receive-activity-designer.md) konusuna bakın.

 [!INCLUDE[crabout](../includes/crabout-md.md)]etkinliği yapılandırmak için **SendReplyToReceive** tasarımcısını <xref:System.ServiceModel.Activities.SendReply> kullanarak aşağıdaki bölüme bakın.

### <a name="properties-of-sendreply"></a>SendReply özellikleri
 Aşağıdaki tablo <xref:System.ServiceModel.Activities.SendReply> özellikleri gösterir ve tasarımcınasıl kullanıldığını açıklar. Bu özellikler özellikleri ızgara düzenlenebilir ve bazı [!INCLUDE[wfd2](../includes/wfd2-md.md)] tasarımcı yüzeyinde düzenlenebilir.

|                               Özellik Adı                                | Gerekli |                                                                                                                                                                                                                                                                                                                                                      Kullanım                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.SendReply> Etkinliğin isteğe bağlı dostu adı. Varsayılan sendReplyToReceive olduğunu.<br /><br /> Dost <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değerin kullanılması kesinlikle gerekli olmasa da, böyle bir değeri kullanmak en iyi yöntemdir.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Bu <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> etkinlikle eşleştirilmiş aktiviteye başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler bir istek/yanıt iletisi deseni modellemek için sunucuda birlikte kullanılır. Bu özellik, hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşlenere olduğunu belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> etkinliği oluşturduğunuz faaliyete otomatik olarak bağlı olduğundan bu özelliği kaldıramazsınız. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Alınacak ileti veya parametre içeriğini belirtir. Bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik ızgarasında **İçerik** alanının yanındaki elips düğmesini tıklatarak veya **Tanımla'yı** tıklatarak bu özelliği düzenleme... **etkinlik** tasarımcısı **yüzeyindeİçerik** etiketinin yanındaki düğmeyi. Her ikisi de **İçerik Tanımı** iletişim kutusunu görüntüler. [!INCLUDE[crabout](../includes/crabout-md.md)]bu kutuyu nasıl kullanacağınız, [İçerik Tanımı İletişim Kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            İş akışı içinde <xref:System.ServiceModel.Activities.CorrelationInitializer> bu <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> etkinliği yapılandıran birden çok nesneyi açan nesnelerin toplanmasını belirtir. <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> **Bağıntı Ekle Initializers** iletişim kutusunu açmak için özellikler ızgarasında ki özelliğin yanındaki elips düğmesini tıklatın. [!INCLUDE[crabout](../includes/crabout-md.md)]bu kutuyu [kullanarak, Bağıntı EkleInitializers İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olarak devam edip etmeyeceğini belirtir. Varsayılan değer **false** şeklindedir.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Gönder](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [GönderGönderAlmaYanıt](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)