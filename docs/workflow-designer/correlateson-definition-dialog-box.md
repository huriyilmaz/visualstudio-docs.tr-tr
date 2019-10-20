---
title: İş Akışı Tasarımcısı-CorrelatesOn tanımı Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650595"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn Tanımı İletişim Kutusu

**CorrelatesOn** iletişim kutusu, bir <xref:System.ServiceModel.Activities.Receive> etkinliğinin <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliğini düzenlemek için iş akışı Tasarımcısı kullanılır. Daha fazla bilgi için bkz. [etkinlik tasarımcısını alma](../workflow-designer/receive-activity-designer.md).

@No__t_0 etkinlikleri arasındaki bağıntı, farklı hizmet işlemlerinin bir iş akışındaki birbirleriyle nasıl bağlanacağını belirtir.

Aşağıdaki tabloda **CorrelatesOn** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|-|-----------------|
|**CorrelatesWith**|İletiyi uygun iş akışı örneğine yönlendirmek için kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|**XPath sorguları**|Gelen iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu değer <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliğine karşılık gelir. XPath sorguları bir <xref:System.ServiceModel.MessageQuerySet> nesnesi içinde bulunur.|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn iletişim kutusunu başlatmak için

**Alma** etkinliği Tasarımcısı **araç kutusu** 'ndan sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, varsayılan alma <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.ServiceModel.Activities.Receive> etkinlik oluşturur. **CorrelatesOn tanımı** iletişim kutusunu açmak için **alma** etkinliği tasarımcısını seçin ve sonra özellik kılavuzunda, **CorrelatesOn** özelliği için koleksiyon metninin yanındaki üç nokta düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializer Ekle İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)