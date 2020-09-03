---
title: Mesajlaşma etkinlik tasarımcıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658930"
---
# <a name="messaging-activity-designers"></a>Mesajlaşma Etkinlik Tasarımcıları
Mesajlaşma etkinliği tasarımcıları, [!INCLUDE[indigo1](../includes/indigo1-md.md)] bir uygulamanın içinden ileti gönderen ve alan mesajlaşma etkinliklerini oluşturmak ve yapılandırmak için kullanılır [!INCLUDE[wf](../includes/wf-md.md)] . , [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] Beş mesajlaşma etkinliği [!INCLUDE[wfd1](../includes/wfd1-md.md)] sunar ve bir iş akışı içinde mesajlaşma yönetmenizi sağlayan iki yeni şablon tasarımcıları sağlar. Bu bölümde yer alan ve aşağıdaki tabloda listelenen konular, [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliğin ve Şablon tasarımcılarının nasıl kullanılacağına ilişkin yönergeler sağlar.

## <a name="in-this-section"></a>Bu Bölümde

|İleti etkinliği|Description|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|<xref:System.ServiceModel.Activities.CorrelationScope>Bir nesne ile alt ileti etkinliklerinin örtük yönetimini sağlayan bir etkinlik oluşturur ve yapılandırır <xref:System.ServiceModel.Activities.CorrelationHandle> .|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|<xref:System.ServiceModel.Activities.InitializeCorrelation>Bir ileti göndermeden veya almadan bağıntı başlatmak için kullanılan bir etkinlik oluşturur ve yapılandırır.|
|[Al](../workflow-designer/receive-activity-designer.md)|<xref:System.ServiceModel.Activities.Receive>Bir hizmetten ileti alan bir etkinlik oluşturur ve yapılandırır.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|<xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Bir etkinlik içinde önceden yapılandırılmış bir çift ve etkinlik oluşturur <xref:System.Activities.Statements.Sequence> .|
|[Gönder](../workflow-designer/send-activity-designer.md)|<xref:System.ServiceModel.Activities.Send>Bir hizmete ileti gönderen bir etkinlik oluşturur ve yapılandırır.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Bir etkinlik içinde önceden yapılandırılmış bir çift ve etkinlik oluşturur <xref:System.Activities.Statements.Sequence> .|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|<xref:System.ServiceModel.Activities.TransactedReceiveScope>İşlemlerin iş akışına akışını sağlayan bir etkinlik oluşturur ve yapılandırır.|

## <a name="reference"></a>Başvuru
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>İlgili Bölümler
 Diğer etkinlik tasarımcıları türleri için aşağıdaki konulara bakın.

 [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)

 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)

 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)

 [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)

 [Temel Türler](../workflow-designer/primitives-activity-designers.md)

 [İşlem](../workflow-designer/transaction-activity-designers.md)

 [Koleksiyon](../workflow-designer/collection-activity-designers.md)

 [Hata Işleme](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Dış Kaynaklar
 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)