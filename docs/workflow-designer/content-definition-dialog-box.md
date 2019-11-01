---
title: İş Akışı Tasarımcısı-Içerik tanımı Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4925d6f6321cd039daca469844ebac6627b08f81
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189793"
---
# <a name="content-definition-dialog-box"></a>İçerik Tanımı İletişim Kutusu

**Içerik tanımı** iletişim kutusu, iş akışı Tasarımcısı <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerin **içerik** özelliklerini yapılandırmak için kullanılır. Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [gönderme](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konularına bakın.

Aşağıdaki tabloda **bağıntı Başlat** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır:

|Arabirim Öğesi|Açıklama|
|-|-----------------|
|**İleti**|İleti **türü** açılan liste kutusunu kullanarak ileti **verisi** ifadesi metin kutusu ve türü ile ileti içeriğini belirtir. Varsayılan olarak, **Içerik tanımı** , iş akışı hizmeti tanımında bir <xref:System.ServiceModel.Channels.Message> veya bir ileti sözleşme türü bekleyen <xref:System.ServiceModel.Activities.ReceiveMessageContent> kullanır.|
|**Parametreler**|Bir veri sözleşmesi bekleyen <xref:System.ServiceModel.Activities.ReceiveParametersContent> kullanmak için **Parametreler** radyo düğmesine tıklayın. Değerleri geçerli iş akışındaki değişken parametrelerine atanan <xref:System.Activities.OutArgument> anahtar/değer çiftleri genel koleksiyonunu ayarlamak için veri kılavuzunu kullanın.|

**Içerik tanımı** Iletişim kutusu **Send**, **Receive**, **ReceiveAndSendReply**ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Bunlara erişmek her durumda benzerdir ve yordamı göstermek için alma durumu burada kullanılır.

**Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu, varsayılan alma <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur. **Al** etkinlik Tasarımcısı ' nı seçin ve **İçerik tanımı** Iletişim kutusunun Özellikler kılavuzundaki **içerik** özelliği için (içerik) metninin yanındaki üç nokta düğmesine tıklayın.

İçerik, bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinliğinin **ileti** bölümünde veya bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinliğinin **parametre** bölümünde belirtilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](browse-and-select-a-dotnet-type-dialog-box.md)