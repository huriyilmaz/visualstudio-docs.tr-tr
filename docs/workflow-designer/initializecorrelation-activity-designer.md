---
title: InitializeCorrelation Etkinlik Tasarımcısı
description: İş Akışı Tasarımcısı, ınitialbağlı bir Ilişki etkinliği oluşturmak ve yapılandırmak için ınitialkayıt Ilişkisi etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 71756f4ed01253607efae47193ea8ddaa6b52a75
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130448"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı

**Initialkayıt ilişkisi** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.InitializeCorrelation> . <xref:System.ServiceModel.Activities.InitializeCorrelation>Etkinlik, iletileri göndermeden veya almadan önce iletiler arasında bir bağıntı kurar.

## <a name="the-initializecorrelation-activity"></a>Initialkaydedilmiş Ilişki etkinliği

Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik, bir ileti göndermeden veya almadan bağıntılar başlatmak için kullanılır. Genellikle bağıntı bir ileti gönderilirken veya alındığında başlatılır. Bir ileti gönderilmeden veya alınmadan önce bağıntı oluşturulmalıdır, <xref:System.ServiceModel.Activities.InitializeCorrelation> bağıntıyı başlatmak için kullanın.

### <a name="using-the-initializecorrelation-activity-designer"></a>Initialkaydedilmiş Ilişki etkinlik tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **ınitialkaydedilmiş Relation** etkinlik tasarımcısına erişin.

**Initialgelsel ilişki** etkinlik Tasarımcısı **araç kutusundan** sürüklenip iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, <xref:System.ServiceModel.Activities.InitializeCorrelation> varsayılan <xref:System.Activities.Activity.DisplayName%2A> ınitialmada ilişkisine sahip bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Initialkaydedilmiş ilişki** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

, <xref:System.ServiceModel.Activities.CorrelationHandle> **Initialsel ilişki** etkinlik Tasarımcısı yüzeyi üzerindeki **Özellikler** penceresinde **bağıntı** alanında belirtilebilir.

İlişki tanıtıcısını ve bunu başlatmak için kullanılan anahtar-değer çiftlerini belirtebileceğiniz **bağıntıyı Başlat** iletişim kutusunu göstermek için **Özellikler** penceresindeki **CorrelationData** alanının yanındaki üç nokta düğmesini seçin. Ya da "görünüm..." i seçin **ınitialsel ilişki** etkinlik Tasarımcısı yüzeyinde ipucu metni. Bu iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesi.

### <a name="the-initializecorrelation-properties"></a>Initialbir Ilişki özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya iş akışı Tasarımcısı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> . Varsayılan değer, ınitialbir Ilişki olur.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir, ancak önerilir.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Yanlış|<xref:System.ServiceModel.Activities.CorrelationHandle>Bağıntı içindeki iş akışı etkinliklerini ilişkilendirmek için kullanılır.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Yanlış|İletileri iş akışı örneğiyle ilişkilendiren bir bağıntı verileri sözlüğü.<br /><br /> Yapılandırmak için **bağıntıyı Başlat** iletişim kutusunu kullanın <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Bu iletişim kutusunu kullan hakkında daha fazla bilgi için, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Al](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Gönder](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)