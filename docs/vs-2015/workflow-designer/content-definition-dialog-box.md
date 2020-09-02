---
title: İçerik tanımı Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656953"
---
# <a name="content-definition-dialog-box"></a>İçerik Tanımı İletişim Kutusu
**İçerik tanımı** iletişim kutusu içinde,,, [!INCLUDE[wfd1](../includes/wfd1-md.md)] **Content** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> ve etkinliklerinin içerik özelliklerini yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanan etkinlik tasarımcıları, [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konularına bakın.

 Aşağıdaki tabloda **bağıntı Başlat** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|----------------|-----------------|
|**İleti**|İleti **türü** açılan liste kutusunu kullanarak ileti **verisi** ifadesi metin kutusu ve türü ile ileti içeriğini belirtir. Varsayılan olarak, **Içerik tanımı** <xref:System.ServiceModel.Activities.ReceiveMessageContent> <xref:System.ServiceModel.Channels.Message> iş akışı hizmeti tanımında bir veya ileti sözleşme türü bekleyen öğesini kullanır.|
|**Parametreler**|Kullanmak için **Parametreler** radyo düğmesine tıklayın <xref:System.ServiceModel.Activities.ReceiveParametersContent> ve bu da veri anlaşması bekler. <xref:System.Activities.OutArgument>Değerleri geçerli iş akışındaki değişken parametrelerine atanmış olan anahtar/değer çiftlerinin genel bir koleksiyonunu ayarlamak için veri kılavuzunu kullanın.|

 **Içerik tanımı** Iletişim kutusu **Send**, **Receive**, **ReceiveAndSendReply**ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Bunlara erişmek her durumda benzerdir ve yordamı göstermek için alma durumu burada kullanılır.

 **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenebilir ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliklerin genellikle yerleştirildiği her yerde yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Receive> , varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . **Al** etkinlik Tasarımcısı ' nı seçin ve **İçerik tanımı** Iletişim kutusunun Özellikler kılavuzundaki **içerik** özelliği için (içerik) metninin yanındaki üç nokta düğmesine tıklayın.

 İçerik, bir etkinliğin **ileti** bölümü içinde <xref:System.ServiceModel.Activities.ReceiveMessageContent> veya bir etkinliğin **parametre** bölümünde belirtilebilir <xref:System.ServiceModel.Activities.ReceiveParametersContent> .

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](../workflow-designer/workflow-designer-ui-help.md)