---
title: Initialbir Ilişki etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659016"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı
**Initialalına ilişkisi** etkinlik Tasarımcısı, iletiler arasında bir bağıntı kurmak için kullanılan bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinliği oluşturmak ve bunları almadan önce yapılandırmak için kullanılır.

## <a name="the-initializecorrelation-activity"></a>Initialkaydedilmiş Ilişki etkinliği
 Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik, bir ileti göndermeden veya almadan bağıntılar başlatmak için kullanılır. Genellikle bağıntı bir ileti gönderilirken veya alındığında başlatılır. Bir ileti gönderilmeden veya alınmadan önce bağıntı oluşturulmalıdır, bağıntıyı başlatmak için <xref:System.ServiceModel.Activities.InitializeCorrelation> kullanın.

### <a name="using-the-initializecorrelation-activity-designer"></a>Initialkaydedilmiş Ilişki etkinlik tasarımcısını kullanma
 **Initialilenlik ilişkisi** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **mesajlaşma** kategorisinde bulunabilir (alternatif olarak, görünümden **araç çubuğu** ' nu seçin).menü veya Ctrl + Alt + X.)

 **Initialgelsel ilişki** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, ınitialmadrelation 'ın varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **ınitialbir ilişki** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

 @No__t_0, **ınitialmadrelation** etkinlik Tasarımcısı yüzeyinde **Özellikler** penceresindeki **bağıntı** alanında belirtilebilir.

 **Özellikler** penceresinde veya "görünüm..." ' de **CorrelationData** alanının yanı sıra elips düğmesine tıklamak **ınitialbir ilişki** etkinlik Tasarımcısı yüzeyinde ipucu metni ' nde, bağıntı tanıtıcısını ve onu başlatmak için kullanılan anahtar-değer çiftlerini belirtebileceğiniz **bağıntıyı Başlat** iletişim kutusu görüntülenir. Bu iletişim kutusunu kullanarak [!INCLUDE[crabout](../includes/crabout-md.md)], [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın.

### <a name="the-initializecorrelation-properties"></a>Initialbir Ilişki özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer, ınitialbir Ilişki olur.<br /><br /> Kolay <xref:System.Activities.Activity.DisplayName%2A> için varsayılan olmayan bir değer kullanımı kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Bağıntı içindeki iş akışı etkinliklerini ilişkilendirmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|İletileri iş akışı örneğiyle ilişkilendiren bir bağıntı verileri sözlüğü.<br /><br /> @No__t_1 yapılandırmak için **bağıntıyı Başlat** iletişim kutusunu kullanın. Bu iletişim kutusunu kullan [!INCLUDE[crabout](../includes/crabout-md.md)], [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)