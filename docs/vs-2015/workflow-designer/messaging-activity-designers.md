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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658930"
---
# <a name="messaging-activity-designers"></a>Mesajlaşma Etkinlik Tasarımcıları
Mesajlaşma etkinliği tasarımcıları, bir [!INCLUDE[wf](../includes/wf-md.md)] uygulamasının içinden [!INCLUDE[indigo1](../includes/indigo1-md.md)] iletileri gönderen ve alan mesajlaşma etkinlikleri oluşturmak ve yapılandırmak için kullanılır. @No__t_0 beş mesajlaşma etkinliği tanıtır ve [!INCLUDE[wfd1](../includes/wfd1-md.md)], bir iş akışı içinde mesajlaşma yönetmenizi sağlayan iki yeni şablon tasarımcıları sağlar. Bu bölümde yer alan ve aşağıdaki tabloda listelenen konular [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliğinin ve Şablon tasarımcılarının nasıl kullanılacağına ilişkin yönergeler sağlar.

## <a name="in-this-section"></a>Bu Bölümde

|İleti etkinliği|Açıklama|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Bir <xref:System.ServiceModel.Activities.CorrelationHandle> nesnesi ile alt ileti etkinliklerinin örtük yönetimi sağlayan <xref:System.ServiceModel.Activities.CorrelationScope> bir etkinlik oluşturur ve yapılandırır.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Bir ileti göndermeden veya almadan bağıntı başlatmak için kullanılan <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik oluşturur ve yapılandırır.|
|[Receive](../workflow-designer/receive-activity-designer.md)|Bir hizmetten ileti alan <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur ve yapılandırır.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|@No__t_2 etkinliğinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri oluşturur.|
|[Send](../workflow-designer/send-activity-designer.md)|Bir hizmete ileti gönderen <xref:System.ServiceModel.Activities.Send> etkinlik oluşturur ve yapılandırır.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|@No__t_2 etkinliğinde önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri oluşturur.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|İşlemlerin iş akışına akışını sağlayan <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik oluşturur ve yapılandırır.|

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

 [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)

 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)

 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)

 [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)

 [Temel Türler](../workflow-designer/primitives-activity-designers.md)

 [İşlem](../workflow-designer/transaction-activity-designers.md)

 [Koleksiyon](../workflow-designer/collection-activity-designers.md)

 [Hata İşleme](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Dış Kaynaklar
 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)