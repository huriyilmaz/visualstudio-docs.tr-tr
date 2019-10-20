---
title: CorrelationScope etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656919"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope Etkinlik Tasarımcısı
**CorrelationScope** etkinlik Tasarımcısı, bir <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesi kullanarak alt ileti etkinliklerinin örtük yönetimi sağlayan <xref:System.ServiceModel.Activities.CorrelationScope> bir etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-correlationscope-activity"></a>CorrelationScope etkinliği
 @No__t_0 özelliği, alt ileti etkinliklerini yönetmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> belirtir. @No__t_2 içindeki <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinlikleri, bağıntı gerçekleştirmek için içeren <xref:System.ServiceModel.Activities.CorrelationScope> etkinliğinin <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> özelliğini kullanacak şekilde yapılandırılmıştır.

### <a name="using-the-correlationscope-activity-designer"></a>CorrelationScope etkinlik tasarımcısını kullanma
 **CorrelationScope** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol **tarafındaki araç** **kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **mesajlaşma** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsü veya Ctrl + Alt + X.)

 **CorrelationScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, varsayılan değer olan CorrelationScope **DisplayName** ile bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinliği oluşturur. @No__t_0, **CorrelationScope** etkinlik tasarımcısının üst bilgisinde veya **Özellikler** penceresinin **DisplayName** kutusunda düzenlenebilir.

 Alt ileti etkinlikleri tarafından kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> belirtmek için, **Özellikler** penceresinde **CorrelatesWith** alanının yanındaki elips düğmesine tıklayarak **ifade Düzenleyicisi** iletişim kutusunu görüntüleyin. Bu özellik, etkinlik Tasarımcısı yüzeyi üzerinde de ayarlanabilir.

 Bağıntı dahilinde olan etkinlikler, kendi tasarımcıların, **CorrelationScope** Designer içindeki **gövde** kutusu içine bırakılarak belirlenir.

### <a name="the-correlationscope-properties"></a>CorrelationScope özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.CorrelationScope> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, **Özellikler** penceresinde veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] tasarımcı yüzeyinde ve genellikle her ikisinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Alt ileti etkinliklerini yönetmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> belirtir. Bu özelliği ayarlanmamışsa, <xref:System.ServiceModel.Activities.CorrelationScope> otomatik olarak örtük bir <xref:System.ServiceModel.Activities.CorrelationHandle> oluşturur.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Bağıntı kapsamındaki etkinlikleri belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Initialbir ilişki](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)