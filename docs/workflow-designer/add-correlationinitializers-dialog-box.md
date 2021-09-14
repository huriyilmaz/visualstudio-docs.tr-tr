---
title: CorrelationInitializers ekle iletişim kutusu
description: Send, Receive ve SendReply etkinliklerinin CorrelationInitializers özelliklerini yapılandırmak için İş Akışı Tasarımcısı'daki Bağıntı Başlatıcıları Ekle iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 4085d8536c9d8f15e8928e010bb2744551a7747c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726078"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializer Ekle İletişim Kutusu

**Bağıntı Başlatıcıları** Ekle iletişim kutusu İş Akışı Tasarımcısı , , ve etkinliklerinin **CorrelationInitializers** özelliklerini <xref:System.ServiceModel.Activities.Send> yapılandırmak için <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> kullanılır. Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [Gönderme,](../workflow-designer/send-activity-designer.md)Alma [,](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply konularına](../workflow-designer/sendandreceivereply-template-designer.md) bakın.

Bu iletişim kutusuyla belirtilen koleksiyonda bağıntı başlatıcıları, mesajlaşma etkinlikleri arasında aşağıdaki bağıntıları başlatabilirsiniz:

- sorgu tabanlı
- bağlam
- geri çağırma bağlamı
- istek-yanıt

Aşağıdaki tabloda Bağıntı Başlatıcıları Ekle iletişim kutusunun kullanıcı arabirimi (UI) **öğeleri** açıklanmış olur:

|Arabirim Öğesi|Description|
|-|-----------------|
|**Başlatıcı Ekleme**|Koleksiyona **ek bir** başlatıcı eklemek için Başlatma ekle kutusuna tıklayın.|
|**Bağıntı Türü**|Bağıntı başlatıcının türünü belirtir. Seçim yapmak için dört tür vardır:<br /><br /> 1. Bir belirtmek için geri çağırma bağıntı <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> başlatıcısı.<br />2. Bir belirtmek için bağlam bağıntı <xref:System.ServiceModel.Activities.CorrelationInitializer> başlatıcısı.<br />3. Belirtmek için istek-yanıt bağıntı <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> başlatıcısı.<br />4. Bir belirtmek için sorgu bağıntı <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> başlatıcısı.<br /><br /> **CorrelationType'i düzenlemek için**<br /><br /> 1. Başlatıcı DataGrid **Ekle'de belirli bir satıra** gidin.<br />2. Odağı **CorrelationTypeComboBox olarak ayarlamak için** Ctrl Tab **tuşlarına** + **basın.**<br />3. **ComboBox'ı** açın ve düzenlemek için Alt+Aşağı tuşlarına basın.|
|**XPath Sorguları**|Gelen ve giden iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu liste yalnızca türleri kullanırken <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> geçerlidir.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Bağıntı Başlatıcıları Ekle iletişim kutusunu başlatmak için

 **Bağıntı Başlatıcıları** Ekle iletişim kutusu **Send**, **Receive**, **ReceiveAndSendReply** ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Her durumda bu verilere erişim de benzerdir ve burada **Receive** tasarımcısını içeren durum yordamı göstermek için kullanılır.

 Alma  etkinliği tasarımcısı Araç Kutusundan **sürüklenip** etkinlikler yerleştirildikten sonra İş Akışı Tasarımcısı yüzeyine bırakılır. Alma etkinlik **tasarımcısını** bırakarak, varsayılan <xref:System.ServiceModel.Activities.Receive> Receive değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. Alma **etkinliği tasarımcısını** seçin ve Bağıntı Başlatıcıları Ekle iletişim kutusunun görünmesi için özellik kılavuzunda  **CorrelationInitializers** özelliğinin (Koleksiyon) metninin yanındaki üç nokta düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)
