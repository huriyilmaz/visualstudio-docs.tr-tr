---
title: InitializeCorrelation Etkinlik Tasarımcısı
description: Bu İş Akışı Tasarımcısı initializeCorrelation etkinlik tasarımcısını kullanarak initializeCorrelation etkinliği oluşturma ve yapılandırma hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: aff2353f0ea681935ff576545f6eb14b957f2c1d58136e240917bd4f86653f75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440506"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı

**InitializeCorrelation etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.ServiceModel.Activities.InitializeCorrelation> kullanılır. Etkinlik, <xref:System.ServiceModel.Activities.InitializeCorrelation> göndermeden veya almadan önce iletiler arasında bir bağıntı sağlar.

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation Etkinliği

Etkinlik, <xref:System.ServiceModel.Activities.InitializeCorrelation> ileti göndermeden veya almadan bağıntıları başlatmak için kullanılır. Genellikle bir ileti göndererek veya alırken bağıntı başlatılır. İleti gönderilmeden veya alınmadan önce bağıntı kurulması gerekirse, <xref:System.ServiceModel.Activities.InitializeCorrelation> bağıntıyı başlatmak için kullanın.

### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısını Kullanma

Araç Kutusunun **Mesajlaşma kategorisinde initializeCorrelation** **etkinlik** tasarımcısına **erişin.**

**InitializeCorrelation** etkinlik tasarımcısı Araç Kutusundan **sürüklenip** bir İş Akışı Tasarımcısı bırakılır. Etkinlik tasarımcısını bırakarak <xref:System.ServiceModel.Activities.InitializeCorrelation> <xref:System.Activities.Activity.DisplayName%2A> initializeCorrelation varsayılan değerine sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **InitializeCorrelation** etkinlik tasarımcısının üst bilgisinde veya Özellikler penceresinin **DisplayName** kutusunda **düzenlenebilir.**

<xref:System.ServiceModel.Activities.CorrelationHandle>, **InitializeCorrelation** **etkinlik** tasarımcısı **yüzeyinin Özellikler** penceresindeki Bağıntı alanında yer alan belirtir.

**Bağıntı tanıtıcıyı** ve bağıntıyı başlatmak için kullanılan anahtar-değer çiftlerini belirtebilirsiniz BağıntıYı Başlat iletişim kutusunu görüntülemek için Özellikler penceresinde **CorrelationData** alanı yanındaki üç nokta **düğmesini** seçin. Veya "Görünüm ..." **InitializeCorrelation etkinlik tasarımcısı yüzeyindeki** ipucu metni. Bu iletişim kutusunu kullanma hakkında daha fazla bilgi için Tür Koleksiyonu [Düzenleyicisi İletişim Kutusu makalesine](../workflow-designer/type-collection-editor-dialog-box.md) bakın.

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation Özellikleri

Aşağıdaki tabloda özellikler <xref:System.ServiceModel.Activities.InitializeCorrelation> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özellikler Özellikler penceresinde veya **İş Akışı Tasarımcısı** düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.ServiceModel.Activities.InitializeCorrelation> adı. Varsayılan değer InitializeCorrelation'dır.<br /><br /> Kolay için varsayılan olmayan bir değerin kullanılması kesinlikle gerekli <xref:System.Activities.Activity.DisplayName%2A> değildir, ancak önerilir.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Yanlış|<xref:System.ServiceModel.Activities.CorrelationHandle>Bağıntıda iş akışı etkinliklerini ilişkilendirmek için kullanılan.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Yanlış|İletileri iş akışı örneğiyle ilişkili bağıntı verileri sözlüğü.<br /><br /> Yapılandırmak **için Bağıntı** Başlat iletişim kutusunu <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> kullanın. Bu iletişim kutusunu kullanma hakkında daha fazla bilgi için Tür Koleksiyonu Düzenleyicisi [İletişim Kutusu makalesine](../workflow-designer/type-collection-editor-dialog-box.md) bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)