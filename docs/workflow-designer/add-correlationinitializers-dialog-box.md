---
title: İş Akışı Tasarımcısı-Correlationbaşlatıcıları Ekle Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d69b53e21d11cba99a9e897871c6f9e0320352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650766"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializer Ekle İletişim Kutusu

@No__t_2, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerinin **correlationbaşlatıcıları** özelliklerini yapılandırmak Için iş akışı Tasarımcısı **bağıntı başlatıcıları Ekle** iletişim kutusu kullanılır. Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [gönderme](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konularına bakın.

Bu iletişim kutusuyla belirtilen koleksiyondaki bağıntı başlatıcıları, mesajlaşma etkinlikleri arasında aşağıdaki bağıntıları başlatabilir:

- Sorgu tabanlı
- bağlam
- geri çağırma bağlamı
- istek-yanıt

Aşağıdaki tabloda **bağıntı başlatıcıları Ekle** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır:

|Arabirim Öğesi|Açıklama|
|-|-----------------|
|**Başlatıcı Ekle**|Koleksiyona ek bir başlatıcı eklemek için **başlatma Ekle** kutusuna tıklayın.|
|**Bağıntı türü**|Bağıntı başlatıcısı türünü belirtir. Aralarından seçim yapabileceğiniz dört tür vardır:<br /><br /> 1. bir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> belirtmek için bir geri çağırma bağıntı başlatıcısı.<br />2. bir <xref:System.ServiceModel.Activities.CorrelationInitializer> belirtmek için bağlam bağıntı başlatıcısı.<br />3. bir istek-bir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> belirtmek için bir istek-yanıt bağıntı başlatıcısı.<br />4. bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> belirtmek için bir sorgu bağıntı başlatıcısı.<br /><br /> **CorrelationType** 'ı düzenlemek için<br /><br /> 1. **ekleme Başlatıcı** DataGrid içindeki belirli bir satıra ait sekme.<br />2. bkz. **CorrelationTypeComboBox**'a odaklanmak için **CTRL** +**Tab**tuşlarına basın.<br />3 **. açılan pencereyi tıklatıp düzenlemek** için alt + aşağı tuşlarına basın.|
|**XPath sorguları**|Gelen ve giden iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu liste yalnızca <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> türleri kullanılırken geçerlidir.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Bağıntı başlatıcıları Ekle iletişim kutusunu başlatmak için

 **Bağıntı başlatıcıları Ekle** iletişim kutusu, **Send**, **Receive**, **ReceiveAndSendReply**ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Bunlara erişmek her durumda benzerdir ve **alma** tasarımcısını içeren durum burada yordamı göstermek için kullanılır.

 **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. **Alma** etkinliği Tasarımcısı ' nın atılması, varsayılan alma <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur. **Alma** etkinliği tasarımcısını seçin ve **bağıntı başlatıcıları Ekle** iletişim kutusunun görünmesi Için özellik kılavuzunda bulunan **correlationbaşlatıcıları** özelliğinin yanındaki üç nokta düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)