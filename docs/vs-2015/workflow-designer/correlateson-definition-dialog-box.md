---
title: CorrelatesOn tanımı Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656947"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn Tanımı İletişim Kutusu
**CorrelatesOn** iletişim kutusu ' de [!INCLUDE[wfd1](../includes/wfd1-md.md)] <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> bir etkinliğin özelliğini düzenlemek için kullanılır <xref:System.ServiceModel.Activities.Receive> . [!INCLUDE[crdefault](../includes/crdefault-md.md)][Al](../workflow-designer/receive-activity-designer.md) konusu.

 Etkinlikler arasındaki bağıntı, <xref:System.ServiceModel.Activities.Receive> farklı hizmet işlemlerinin bir iş akışındaki birbirleriyle nasıl bağlanacağını belirtir.

 Aşağıdaki tabloda **CorrelatesOn** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>İletiyi uygun iş akışı örneğine yönlendirmek için kullanılır.|
|**XPath sorguları**|Gelen iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu, özelliğine karşılık gelir <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> . XPath sorguları bir nesnesi içinde bulunur <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn iletişim kutusunu başlatmak için
 **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenebilir ve [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinliklerin genellikle yerleştirildiği her yerde yüzeyine bırakılabilir. Bu <xref:System.ServiceModel.Activities.Receive> , varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . **Al** etkinlik Tasarımcısı ' nı seçin ve **CorrelatesOn tanımı** Iletişim kutusunun özellik kılavuzunda **CorrelatesOn** özelliği için (koleksiyon) metninin yanındaki üç nokta düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.ServiceModel.Activities.Receive>[Correlationbaşlatıcıları Ekle Iletişim kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md) [bağıntı Başlat iletişim kutusu](../workflow-designer/initialize-correlation-dialog-box.md)