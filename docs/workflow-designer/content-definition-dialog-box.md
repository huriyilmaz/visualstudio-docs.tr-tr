---
title: İş Akışı Tasarımcısı - İçerik Tanımı İletişim Kutusu
description: Gönder, Al, GönderReply ve ReceiveReply etkinliklerinin İçerik özelliklerini yapılandırmak için İçerik Tanımı iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: b3432853ce9e6aaf4f37c4a0c363099f4a61d988
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633702"
---
# <a name="content-definition-dialog-box"></a>İçerik Tanımı İletişim Kutusu

İçerik **Tanımı iletişim** kutusu İş Akışı Tasarımcısı , , ve  etkinliklerinin İçerik özelliklerini yapılandırmak <xref:System.ServiceModel.Activities.Send> için <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> kullanılır. Bu kutuyu kullanan etkinlik tasarımcıları hakkında daha fazla bilgi için [Gönderme,](../workflow-designer/send-activity-designer.md)Alma [,](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)ve [SendAndReceiveReply konularına](../workflow-designer/sendandreceivereply-template-designer.md) bakın.

Aşağıdaki tabloda Bağıntı Başlat iletişim kutusunun kullanıcı arabirimi (UI) **öğeleri** açık almaktadır:

|Arabirim Öğesi|Description|
|-|-----------------|
|**İleti**|İleti türü açılan liste **kutusunu kullanarak** İleti veri ifadesi metin kutusu ile ileti içeriğini **ve** türünü belirtir. varsayılan olarak, **İçerik Tanımı,** iş akışı <xref:System.ServiceModel.Activities.ReceiveMessageContent> hizmet tanımı içinde bir veya ileti sözleşme türü bekler olan <xref:System.ServiceModel.Channels.Message> kullanır.|
|**Parametreler**|Kullanmak **için Parametreler** radyo düğmesine <xref:System.ServiceModel.Activities.ReceiveParametersContent> tıklayın. Bu düğme bir veri sözleşmesi bekler. Değerleri geçerli iş akışındaki değişken parametrelere atanmış olan anahtar/değer çiftlerinin genel <xref:System.Activities.OutArgument> koleksiyonunu ayarlamak için veri kılavuzu kullanın.|

İçerik **Tanımı iletişim** kutusu Send **,** **Receive**, **ReceiveAndSendReply** ve **SendAndReceiveReply** tasarımcıları tarafından kullanılır. Her durumda erişim benzerdir ve burada Alma büyük/küçük harf yordamını göstermek için kullanılır.

Alma  etkinliği tasarımcısı, Etkinlikler genellikle yerleştirildikten sonra **Araç** Kutusundan sürüklenip İş Akışı Tasarımcısı yüzeyine bırakılır. Bu, varsayılan <xref:System.ServiceModel.Activities.Receive> Alma değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. Alma **etkinliği** tasarımcısını seçin ve İçerik Tanımı iletişim kutusunun görünmesi için özellik kılavuzunda **content** özelliğinin (İçerik) metninin yanındaki üç nokta düğmesine tıklayın. 

İçerik, bir etkinliğin **İleti** bölümünde veya <xref:System.ServiceModel.Activities.ReceiveMessageContent> bir etkinliğin **Parametre** bölümünde <xref:System.ServiceModel.Activities.ReceiveParametersContent> belirtilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](browse-and-select-a-dotnet-type-dialog-box.md)