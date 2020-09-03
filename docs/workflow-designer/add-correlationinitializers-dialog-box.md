---
title: İş Akışı Tasarımcısı-Correlationbaşlatıcıları Ekle Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2a0b0f7c76b392d5d2d0135c3ab6e370f8678e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114301"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializer Ekle İletişim Kutusu

**Bağıntı başlatıcıları Ekle** iletişim kutusu,,, ve etkinliklerinin **correlationbaşlatıcıları** özelliklerini yapılandırmak için iş akışı Tasarımcısı kullanılır <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> . Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [gönderme](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konularına bakın.

Bu iletişim kutusuyla belirtilen koleksiyondaki bağıntı başlatıcıları, mesajlaşma etkinlikleri arasında aşağıdaki bağıntıları başlatabilir:

- Sorgu tabanlı
- bağlam
- geri çağırma bağlamı
- istek-yanıt

Aşağıdaki tabloda **bağıntı başlatıcıları Ekle** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır:

|Arabirim Öğesi|Description|
|-|-----------------|
|**Başlatıcı Ekle**|Koleksiyona ek bir başlatıcı eklemek için **başlatma Ekle** kutusuna tıklayın.|
|**Bağıntı türü**|Bağıntı başlatıcısı türünü belirtir. Aralarından seçim yapabileceğiniz dört tür vardır:<br /><br /> 1. belirtmek için bir geri çağırma bağıntı Başlatıcısı <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. belirtmek için bir bağlam bağıntı Başlatıcısı <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. bir istek-bir belirtmek için bağıntı başlatıcısı yanıtlayın <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. belirtmek için bir sorgu bağıntı Başlatıcısı <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> **CorrelationType** 'ı düzenlemek için<br /><br /> 1. **ekleme Başlatıcı** DataGrid içindeki belirli bir satıra ait sekme.<br />2. bkz. **CorrelationTypeComboBox**'a odaklanmak için **CTRL**tuşuna basın + **Tab**.<br />3 **. açılan pencereyi tıklatıp düzenlemek** için alt + aşağı tuşlarına basın.|
|**XPath sorguları**|Gelen ve giden iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu liste yalnızca türler kullanılırken geçerlidir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Bağıntı başlatıcıları Ekle iletişim kutusunu başlatmak için

 **Bağıntı başlatıcıları Ekle** iletişim kutusu, **Send**, **Receive**, **ReceiveAndSendReply**ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Bunlara erişmek her durumda benzerdir ve **alma** tasarımcısını içeren durum burada yordamı göstermek için kullanılır.

 **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. **Alma** etkinliği Tasarımcısı ' nın atılması, <xref:System.ServiceModel.Activities.Receive> Varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . **Alma** etkinliği tasarımcısını seçin ve **bağıntı başlatıcıları Ekle** iletişim kutusunun görünmesi Için özellik kılavuzunda bulunan **correlationbaşlatıcıları** özelliğinin yanındaki üç nokta düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)
