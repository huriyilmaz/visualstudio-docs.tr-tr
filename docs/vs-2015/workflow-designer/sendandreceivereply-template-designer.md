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
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395338"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı
**SendAndReceiveReply** şablonu, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> istemcideki bir <xref:System.Activities.Statements.Sequence> istek/yanıt iletisi değişim deseninin parçası olarak bağıntılı bir etkinlik içinde önceden yapılandırılmış ve etkinlik çifti oluşturmak için kullanılır.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablonu
 **SendAndReceiveReply** şablonu eklemek, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> bir etkinlik içinde ve etkinliklerini oluşturmanın yanı sıra üç şey yapar <xref:System.Activities.Statements.Sequence> :

1. <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> Etkinliğin özelliklerini yapılandırır <xref:System.ServiceModel.Activities.Send> .

2. <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> <xref:System.ServiceModel.Activities.ReceiveReply> Etkinliğin özelliğini etkinliğe bağlar <xref:System.ServiceModel.Activities.Send> .

3. <xref:System.ServiceModel.Activities.CorrelationHandle>Üst etkinlikte bir değişken olarak oluşturur.

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon tasarımcısını kullanma
 **SendAndReceiveReply** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak **Messaging** erişilen (alternatif olarak **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] , **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.) iletişim kutusunun mesajlaşma kategorisinde bulunabilir.

 **SendAndReceiveReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliklerin genellikle yerleştirilme her yerde yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Send> , **Send** Activity Designer ile yapılandırılabilen bir etkinlik ve <xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend** Tasarımcısı ile yapılandırılabilecek bir bağıntılı oluşturur.

 [!INCLUDE[crabout](../includes/crabout-md.md)] etkinliği yapılandırmak için **Gönder** tasarımcısını kullanarak <xref:System.ServiceModel.Activities.Send> , [Gönder](../workflow-designer/send-activity-designer.md) konusuna bakın.

 [!INCLUDE[crabout](../includes/crabout-md.md)] etkinliğini yapılandırmak için **ReceiveReplyForSend** tasarımcısını kullanarak <xref:System.ServiceModel.Activities.ReceiveReply> aşağıdaki bölüme bakın.

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|                                 Özellik Adı                                 | Gerekli |                                                                                                                                                                                                                                                                                                                                                        Kullanım                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Yanlış   |                                                                                                                                                                                            Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.ReceiveReply> . Varsayılan değer ReceiveReplyForSend ' dir.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Doğru   | <xref:System.ServiceModel.Activities.Send>Bu etkinlikle eşleştirilmiş etkinliğe başvuru <xref:System.ServiceModel.Activities.ReceiveReply> . Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri, istemci üzerinde bir istek/yanıt mesajlaşma modelini modellemek için birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmek gerektiğini belirtir. Tasarımcıda Bu özelliği düzenleyemezsiniz, çünkü <xref:System.ServiceModel.Activities.Send> etkinliği oluşturduğunuz etkinliğe otomatik olarak bağlanır <xref:System.ServiceModel.Activities.ReceiveReply> . |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Yanlış   |                        Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki elips düğmesine tıklayarak veya **tanımla...** öğesine tıklayarak bu özelliği düzenleyin. **Al** etkinlik Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki düğme. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanarak, [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Yanlış   |              <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanarak, [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Yanlış   |                                                                                                                                                                                                                                               İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [ınitialkaydedilmiş ilişkisi](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)