---
title: SendAndReceiveReply şablon Tasarımcısı | Microsoft Docs
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
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663276"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı
**SendAndReceiveReply** şablonu, istemci üzerindeki istek/yanıt iletisi değişim deseninin bir parçası olarak bağıntılı bir <xref:System.Activities.Statements.Sequence> etkinliği içinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerini oluşturmak için kullanılır.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu
 **SendAndReceiveReply** şablonu eklemek, bir <xref:System.Activities.Statements.Sequence> etkinliği içinde <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerini oluşturmanın yanı sıra üç şey yapar:

1. @No__t_2 etkinliğinin <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> özelliklerini yapılandırır.

2. @No__t_1 etkinliğinin <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğini <xref:System.ServiceModel.Activities.Send> etkinliğine bağlar.

3. Üst etkinlikte değişken olarak bir <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon tasarımcısını kullanma
 **SendAndReceiveReply** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif **olarak,** **görünümde** **araç çubuğu** sekmesine tıklanarak erişilen) **araç kutusunun** **mesajlaşma** kategorisinde bulunabilir. menü veya CTRL + ALT + X.)

 **SendAndReceiveReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, **Send** Activity Designer ile yapılandırılabilen bir <xref:System.ServiceModel.Activities.Send> etkinlik ve **ReceiveReplyForSend** Tasarımcısı ile yapılandırılabilecek bağıntılı bir <xref:System.ServiceModel.Activities.ReceiveReply> oluşturur.

 <xref:System.ServiceModel.Activities.Send> etkinliğini yapılandırmak için **Gönder** tasarımcısını [!INCLUDE[crabout](../includes/crabout-md.md)], [Gönder](../workflow-designer/send-activity-designer.md) konusuna bakın.

 [!INCLUDE[crabout](../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini yapılandırmak için **ReceiveReplyForSend** tasarımcısını kullanarak aşağıdaki bölüme bakın.

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer yüzeyinde düzenlenebilir.

|                                 Özellik adı                                 | Gerekli |                                                                                                                                                                                                                                                                                                                                                        Kullanım                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            @No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer ReceiveReplyForSend ' dir.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Doğru   | Bu <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğiyle eşleştirilmiş <xref:System.ServiceModel.Activities.Send> etkinliğine başvuru. Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri, istemci üzerinde bir istek/yanıt mesajlaşma modelini modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğinin eşleştirilmek gerektiğini belirtir. Tasarımcıda, <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini oluşturduğunuz <xref:System.ServiceModel.Activities.Send> etkinliğe otomatik olarak bağlandığından bu özelliği düzenleyemezsiniz. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Alacak ileti veya parametre içeriğini belirtir. @No__t_0 bir etkinlik veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliği olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki elips düğmesine tıklayarak veya **tanımla...** öğesine tıklayarak bu özelliği düzenleyin. **Al** etkinlik Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki düğme. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. Bu kutuyu nasıl kullanacağınızı [!INCLUDE[crabout](../includes/crabout-md.md)], [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Bu <xref:System.ServiceModel.Activities.Receive> etkinliğini iş akışı içinde yapılandıran birden çok <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesini başlatacak <xref:System.ServiceModel.Activities.CorrelationInitializer> nesnelerinin koleksiyonunu belirtir. Özellikler kılavuzundaki <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliğinin yanındaki üç nokta düğmesine tıklayarak **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. Bu kutuyu kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)], [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> <strong>https://tempuri.org/{service sözleşme ad alanı}/{Service sözleşme adı}/{Operation Name}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [ınitialkaydedilmiş ilişkisi](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)