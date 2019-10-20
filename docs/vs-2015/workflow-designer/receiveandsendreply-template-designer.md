---
title: ReceiveAndSendReply şablon Tasarımcısı | Microsoft Docs
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
ms.openlocfilehash: e853967f73c99aa52958754e9f59f644c2f9497b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672549"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı
**ReceiveAndSendReply** şablonu, sunucuda bir istek/yanıt iletisi değişim deseninin parçası olarak bağıntılı bir <xref:System.Activities.Statements.Sequence> etkinliği içinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerini oluşturmak için kullanılır.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu
 **ReceiveAndSendReply** şablonu eklemek, bir <xref:System.Activities.Statements.Sequence> etkinliğiyle <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerini oluşturmanın yanı sıra üç şey yapar:

1. @No__t_2 etkinliğinin <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> özelliklerini yapılandırır.

2. @No__t_1 etkinliğinin <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Send> etkinliğine bağlar.

3. Üst etkinlikte değişken olarak bir <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon tasarımcısını kullanma
 **ReceiveAndSendReply** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **görünümden** **araç çubuğu** sekmesine tıklanarak erişilen) **araç kutusunun** **mesajlaşma** kategorisinde bulunabilir. menü veya CTRL + ALT + X.)

 **ReceiveAndSendReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, **gönderme** etkinliği Tasarımcısı ile yapılandırılabilen bir <xref:System.ServiceModel.Activities.Receive> etkinlik ve SendReplyToReceive Tasarımcısı ile yapılandırılabilecek bağıntılı bir <xref:System.ServiceModel.Activities.SendReply> oluşturur.

 <xref:System.ServiceModel.Activities.Receive> etkinliğini yapılandırmak için **alma** tasarımcısını kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)] [alma](../workflow-designer/receive-activity-designer.md) konusuna bakın.

 <xref:System.ServiceModel.Activities.SendReply> etkinliğini yapılandırmak için **SendReplyToReceive** tasarımcısını kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)] aşağıdaki bölüme bakın.

### <a name="properties-of-sendreply"></a>SendReply özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.SendReply> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] tasarımcı yüzeyinde düzenlenebilir.

|                               Özellik adı                                | Gerekli |                                                                                                                                                                                                                                                                                                                                                      Kullanım                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            @No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer SendReplyToReceive ' dir.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Doğru   | Bu <xref:System.ServiceModel.Activities.SendReply> etkinliğiyle eşleştirilmiş <xref:System.ServiceModel.Activities.Receive> etkinliğine başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, sunucu üzerinde bir istek/yanıt mesajlaşma modeli modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğinin eşleştirilmek gerektiğini belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.SendReply> etkinliğini oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğe otomatik olarak bağlandığından bu özelliği düzenleyemezsiniz. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Alacak ileti veya parametre içeriğini belirtir. @No__t_0 bir etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliği olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki elips düğmesine tıklayarak veya **tanımla...** öğesine tıklayarak bu özelliği düzenleyin. **Al** etkinlik Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki düğme. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutuyu nasıl kullanacağınızı [!INCLUDE[crabout](../includes/crabout-md.md)], [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Bu <xref:System.ServiceModel.Activities.Receive> etkinliğini iş akışı içinde yapılandıran birden çok <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesini başlatacak <xref:System.ServiceModel.Activities.CorrelationInitializer> nesnelerinin koleksiyonunu belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)], [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> <strong>https://tempuri.org/{service sözleşme ad alanı}/{Service sözleşme adı}/{Operation Name}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olup olmayacağını belirtir. Varsayılan değer **false**'dur.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [ınitialkaydedilmiş ilişki](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) gönder