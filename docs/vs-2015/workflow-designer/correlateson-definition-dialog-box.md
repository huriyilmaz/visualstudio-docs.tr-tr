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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656947"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn Tanımı İletişim Kutusu
**CorrelatesOn** iletişim kutusu, bir <xref:System.ServiceModel.Activities.Receive> etkinliğinin <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliğini düzenlemek için [!INCLUDE[wfd1](../includes/wfd1-md.md)] kullanılır. [alma](../workflow-designer/receive-activity-designer.md) konusunu [!INCLUDE[crdefault](../includes/crdefault-md.md)].

 @No__t_0 etkinlikleri arasındaki bağıntı, farklı hizmet işlemlerinin bir iş akışındaki birbirleriyle nasıl bağlanacağını belirtir.

 Aşağıdaki tabloda **CorrelatesOn** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|----------------|-----------------|
|**CorrelatesWith**|İletiyi uygun iş akışı örneğine yönlendirmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|**XPath sorguları**|Gelen iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu, <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliğine karşılık gelir. XPath sorguları bir <xref:System.ServiceModel.MessageQuerySet> nesnesi içinde bulunur.|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn iletişim kutusunu başlatmak için
 **Alma** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, etkinliklerin genellikle yerleştirildiği her yerde [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. Bu, varsayılan alma <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur. **Al** etkinlik Tasarımcısı ' nı seçin ve **CorrelatesOn tanımı** Iletişim kutusunun özellik kılavuzunda **CorrelatesOn** özelliği için (koleksiyon) metninin yanındaki üç nokta düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.ServiceModel.Activities.Receive> [Correlationbaşlatıcıları Ekle iletişim](../workflow-designer/add-correlationinitializers-dialog-box.md) kutusu [bağıntı Başlat iletişim kutusu](../workflow-designer/initialize-correlation-dialog-box.md)