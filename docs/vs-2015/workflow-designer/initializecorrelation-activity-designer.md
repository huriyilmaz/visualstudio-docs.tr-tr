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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659016"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı
**Initialalına ilişkisi** etkinlik Tasarımcısı, <xref:System.ServiceModel.Activities.InitializeCorrelation> iletiler arasında ilişki kurmak için kullanılan bir etkinlik oluşturmak ve onları almadan önce yapılandırmak için kullanılır.

## <a name="the-initializecorrelation-activity"></a>Initialkaydedilmiş Ilişki etkinliği
 Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik, bir ileti göndermeden veya almadan bağıntılar başlatmak için kullanılır. Genellikle bağıntı bir ileti gönderilirken veya alındığında başlatılır. Bir ileti gönderilmeden veya alınmadan önce bağıntı oluşturulmalıdır, <xref:System.ServiceModel.Activities.InitializeCorrelation> bağıntıyı başlatmak için kullanın.

### <a name="using-the-initializecorrelation-activity-designer"></a>Initialkaydedilmiş Ilişki etkinlik tasarımcısını kullanma
 **Initialilenlik ilişkisi** etkinlik Tasarımcısı **, araç kutusunun** **ileti** kategorisinde bulunabilir. Buna alternatif olarak, **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** sekmesine tıklanarak veya Ctrl + Alt + X ' i seçin.)

 **Initialgelsel ilişki** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.InitializeCorrelation> , varsayılan ınitialbağlı bir ilişki olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . Bu, <xref:System.Activities.Activity.DisplayName%2A> **ınitialoluştura ilişkisi** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

 , <xref:System.ServiceModel.Activities.CorrelationHandle> **Initialsel ilişki** etkinlik Tasarımcısı yüzeyi üzerindeki **Özellikler** penceresinde **bağıntı** alanında belirtilebilir.

 **Özellikler** penceresinde veya "görünüm..." ' de **CorrelationData** alanının yanı sıra elips düğmesine tıklamak **ınitialbir ilişki** etkinlik Tasarımcısı yüzeyinde ipucu metni ' nde, bağıntı tanıtıcısını ve onu başlatmak için kullanılan anahtar-değer çiftlerini belirtebileceğiniz **bağıntıyı Başlat** iletişim kutusu görüntülenir. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu iletişim kutusunu kullanarak, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın.

### <a name="the-initializecorrelation-properties"></a>Initialbir Ilişki özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> . Varsayılan değer, ınitialbir Ilişki olur.<br /><br /> Kolay için varsayılan olmayan bir değer kullanılması <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bu tür bir değer kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Yanlış|<xref:System.ServiceModel.Activities.CorrelationHandle>Bağıntı içindeki iş akışı etkinliklerini ilişkilendirmek için kullanılır.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Yanlış|İletileri iş akışı örneğiyle ilişkilendiren bir bağıntı verileri sözlüğü.<br /><br /> Yapılandırmak için **bağıntıyı Başlat** iletişim kutusunu kullanın <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . [!INCLUDE[crabout](../includes/crabout-md.md)] Bu iletişim kutusunu kullanın, [tür koleksiyonu Düzenleyicisi Iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konusuna bakın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)