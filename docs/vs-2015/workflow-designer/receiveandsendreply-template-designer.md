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
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395387"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı
**ReceiveAndSendReply** şablonu, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> sunucuda bir istek/yanıt iletisi değişim deseninin parçası olarak bağıntılı bir etkinlik içinde önceden yapılandırılmış ve etkinliklerin çiftini oluşturmak için kullanılır.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablonu
 **ReceiveAndSendReply** şablonu eklemek, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerini bir etkinlik ile oluşturmanın yanı sıra üç şey yapar <xref:System.Activities.Statements.Sequence> :

1. <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> Etkinliğin özelliklerini yapılandırır <xref:System.ServiceModel.Activities.Receive> .

2. <xref:System.ServiceModel.Activities.SendReply.Request%2A> <xref:System.ServiceModel.Activities.Receive> Etkinliğin özelliğini etkinliğe bağlar <xref:System.ServiceModel.Activities.Send> .

3. <xref:System.ServiceModel.Activities.CorrelationHandle>Üst etkinlikte bir değişken olarak oluşturur.

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon tasarımcısını kullanma
 **ReceiveAndSendReply** etkinlik Tasarımcısı, ' deki araç **kutusu** sekmesine tıklanarak erişilen araç **kutusunun** **mesajlaşma** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 **ReceiveAndSendReply** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliklerin genellikle yerleştirildiği her yerde yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Receive> , **gönderme** etkinliği Tasarımcısı ile yapılandırılabilecek bir etkinlik ve <xref:System.ServiceModel.Activities.SendReply> SendReplyToReceive Tasarımcısı ile yapılandırılabilecek bir bağıntılı oluşturur.

 [!INCLUDE[crabout](../includes/crabout-md.md)] etkinliği yapılandırmak için **alma** tasarımcısını kullanarak <xref:System.ServiceModel.Activities.Receive> [alma](../workflow-designer/receive-activity-designer.md) konusuna bakın.

 [!INCLUDE[crabout](../includes/crabout-md.md)] etkinliği yapılandırmak için **SendReplyToReceive** tasarımcısını kullanarak <xref:System.ServiceModel.Activities.SendReply> aşağıdaki bölüme bakın.

### <a name="properties-of-sendreply"></a>SendReply özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.SendReply> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, Özellikler kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|                               Özellik Adı                                | Gerekli |                                                                                                                                                                                                                                                                                                                                                      Kullanım                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Yanlış   |                                                                                                                                                                                            Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.SendReply> . Varsayılan değer SendReplyToReceive ' dir.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Doğru   | <xref:System.ServiceModel.Activities.Receive>Bu etkinlikle eşleştirilmiş etkinliğe başvuru <xref:System.ServiceModel.Activities.SendReply> . Bu özellik **null**olmamalıdır. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, istek/yanıt mesajlaşma modelini modellemek için sunucuda birlikte kullanılır. Bu özellik hangi <xref:System.ServiceModel.Activities.Send> etkinliğin eşleştirilmek gerektiğini belirtir. Tasarımcıda Bu özelliği düzenleyemezsiniz, çünkü <xref:System.ServiceModel.Activities.Send> etkinliği oluşturduğunuz etkinliğe otomatik olarak bağlanır <xref:System.ServiceModel.Activities.SendReply> . |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Yanlış   |                       Alacak ileti veya parametre içeriğini belirtir. <xref:System.ServiceModel.Activities.ReceiveMessageContent>Etkinlik ya da <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik olabilir. Özellik kılavuzundaki **içerik** alanının yanındaki elips düğmesine tıklayarak veya **tanımla...** öğesine tıklayarak bu özelliği düzenleyin. **Al** etkinlik Tasarımcısı yüzeyinde **içerik** etiketinin yanındaki düğme. Her ikisi de **Içerik tanımı** iletişim kutusunu görüntüler. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanarak, [Içerik tanımı Iletişim kutusu](../workflow-designer/content-definition-dialog-box.md) konusuna bakın.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Yanlış   |            <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle> Bu <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde yapılandıran birden çok nesneyi başlatacak nesne koleksiyonunu belirtir. Özellikler kılavuzundaki özelliğin yanındaki üç nokta düğmesine tıklayarak <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> **bağıntı başlatıcıları Ekle** iletişim kutusunu açın. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanarak, [Correlationbaşlatıcıları ekleme Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) konusuna bakın.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Yanlış   |                                                                                                                                                                                                                                              İletinin eylem üst bilgisini belirtir. Açıkça ayarlanmamışsa, değeri varsayılan olarak şu şekilde ayarlanır:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Yanlış   |                                                                                                                                                                                                                                                                                          Yanıt iletisi gönderilmeden önce iş akışı örneğinin kalıcı olup olmayacağını belirtir. Varsayılan değer **false** şeklindedir.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [ınitialkaydedilmiş ilişki](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) gönder