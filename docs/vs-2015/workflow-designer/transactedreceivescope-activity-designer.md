---
title: TransactedReceiveScope etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4230e4b598553f5fefbc3b97663fd42320ee1e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607012"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı
**TransactedReceiveScope** Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope etkinliği
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik, bir işlemi iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemlerine akabilmenizi sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik tasarımcısını kullanma
 **TransactedReceiveScope** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak **Messaging** erişilen (alternatif olarak **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] , **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçerek) iletişim kutusunun mesajlaşma kategorisinde bulunabilir.

 **TransactedReceiveScope** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliklerin genellikle yerleştirildiği her yerde yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.TransactedReceiveScope> , TransactedReceiveScope 'un varsayılan **DisplayName** 'i olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TransactedReceiveScope** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

 **TransactedReceiveScope** Tasarımcısı **istek** ve **gövde** kutularını içerir. Bunlar <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> , bir <xref:System.ServiceModel.Activities.Receive> etkinliği ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> diğerini belirten özelliği belirleyen özelliği yapılandırmak için kullanılır <xref:System.Activities.Activity> . , <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Bir işlem oluşturur. Daha sonra işlem, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> Bu kapsamdaki herhangi bir etkinliğin bu işlem içinde yürütüldüğü şekilde öğesinin kapsamı için çevresel hale getirilir.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope özellikleri
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.TransactedReceiveScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu <xref:System.Activities.Activity.DisplayName%2A> özellik, özellik kılavuzunda veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyde düzenlenebilir, ancak diğerleri tasarım yüzeyinde düzenlenmelidir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Varsayılan değer TransactedReceiveScope ' dir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|<xref:System.ServiceModel.Activities.Receive>Etkinlik Tasarımcısı yüzeyinde bir etkinliği **istek** bloğuna bırakır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Yanlış|<xref:System.Activities.Activity>Etkinlik Tasarımcısı yüzeyinde **gövde** bloğunun içine bırakır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [ınitialkaydedilmiş ilişkisi](../workflow-designer/initializecorrelation-activity-designer.md) [alma](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) gönder