---
title: İş Akışı Tasarımcısı-Içerik tanımı Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19e2341d458c98f01d3b58d6f77887ac1cfe6746
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876209"
---
# <a name="content-definition-dialog-box"></a>İçerik Tanımı İletişim Kutusu

**İçerik tanımı** iletişim kutusu,,, **Content** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> ve etkinliklerinin içerik özelliklerini yapılandırmak için iş akışı Tasarımcısı kullanılır <xref:System.ServiceModel.Activities.ReceiveReply> . Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [gönderme](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konularına bakın.

Aşağıdaki tabloda **bağıntı Başlat** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır:

|Arabirim Öğesi|Açıklama|
|-|-----------------|
|**İleti**|İleti **türü** açılan liste kutusunu kullanarak ileti **verisi** ifadesi metin kutusu ve türü ile ileti içeriğini belirtir. Varsayılan olarak, **Içerik tanımı** <xref:System.ServiceModel.Activities.ReceiveMessageContent> <xref:System.ServiceModel.Channels.Message> iş akışı hizmeti tanımında bir veya ileti sözleşme türü bekleyen öğesini kullanır.|
|**Parametreler**|Kullanmak için **Parametreler** radyo düğmesine tıklayın <xref:System.ServiceModel.Activities.ReceiveParametersContent> ve bu da veri anlaşması bekler. <xref:System.Activities.OutArgument>Değerleri geçerli iş akışındaki değişken parametrelerine atanmış olan anahtar/değer çiftlerinin genel bir koleksiyonunu ayarlamak için veri kılavuzunu kullanın.|

**Içerik tanımı** Iletişim kutusu **Send**, **Receive**, **ReceiveAndSendReply**ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Bunlara erişmek her durumda benzerdir ve yordamı göstermek için alma durumu burada kullanılır.

**Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Receive> , varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . **Al** etkinlik Tasarımcısı ' nı seçin ve **İçerik tanımı** Iletişim kutusunun Özellikler kılavuzundaki **içerik** özelliği için (içerik) metninin yanındaki üç nokta düğmesine tıklayın.

İçerik, bir etkinliğin **ileti** bölümü içinde <xref:System.ServiceModel.Activities.ReceiveMessageContent> veya bir etkinliğin **parametre** bölümünde belirtilebilir <xref:System.ServiceModel.Activities.ReceiveParametersContent> .

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](browse-and-select-a-dotnet-type-dialog-box.md)