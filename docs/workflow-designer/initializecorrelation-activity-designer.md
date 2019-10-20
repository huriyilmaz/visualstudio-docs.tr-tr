---
title: İş Akışı Tasarımcısı-ınitialkaydedilmiş Ilişki etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650220"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı

**Initialkayıt ilişkisi** etkinlik Tasarımcısı <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik oluşturmak ve yapılandırmak için kullanılır. @No__t_0 etkinliği iletileri göndermeden veya almadan önce iletiler arasında bir bağıntı kurar.

## <a name="the-initializecorrelation-activity"></a>Initialkaydedilmiş Ilişki etkinliği

Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik, bir ileti göndermeden veya almadan bağıntılar başlatmak için kullanılır. Genellikle bağıntı bir ileti gönderilirken veya alındığında başlatılır. Bir ileti gönderilmeden veya alınmadan önce bağıntı oluşturulmalıdır, bağıntıyı başlatmak için <xref:System.ServiceModel.Activities.InitializeCorrelation> kullanın.

### <a name="using-the-initializecorrelation-activity-designer"></a>Initialkaydedilmiş Ilişki etkinlik tasarımcısını kullanma

**Araç kutusunun** **mesajlaşma** kategorisindeki **ınitialkaydedilmiş Relation** etkinlik tasarımcısına erişin.

**Initialgelsel ilişki** etkinlik Tasarımcısı **araç kutusundan** sürüklenip iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, ınitialmadrelation 'ın varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik oluşturur. @No__t_0, **ınitialbir ilişki** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

@No__t_0, **ınitialmadrelation** etkinlik Tasarımcısı yüzeyinde **Özellikler** penceresindeki **bağıntı** alanında belirtilebilir.

İlişki tanıtıcısını ve bunu başlatmak için kullanılan anahtar-değer çiftlerini belirtebileceğiniz **bağıntıyı Başlat** iletişim kutusunu göstermek için **Özellikler** penceresindeki **CorrelationData** alanının yanındaki üç nokta düğmesini seçin. Ya da "görünüm..." i seçin **ınitialsel ilişki** etkinlik Tasarımcısı yüzeyinde ipucu metni. Bu iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesi.

### <a name="the-initializecorrelation-properties"></a>Initialbir Ilişki özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya iş akışı Tasarımcısı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer, ınitialbir Ilişki olur.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanılması kesinlikle gerekli değildir, ancak önerilir.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Bağıntı içindeki iş akışı etkinliklerini ilişkilendirmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|İletileri iş akışı örneğiyle ilişkilendiren bir bağıntı verileri sözlüğü.<br /><br /> @No__t_1 yapılandırmak için **bağıntıyı Başlat** iletişim kutusunu kullanın. Bu iletişim kutusunu kullan hakkında daha fazla bilgi için, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)