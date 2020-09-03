---
title: İş Akışı Tasarımcısı-CorrelatesOn tanımı Iletişim kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d2db5bbfa4f34d86d3bf20cfe6bcc42b3dc00d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876131"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn Tanımı İletişim Kutusu

**CorrelatesOn** iletişim kutusu, <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> bir etkinliğin özelliğini düzenlemek için iş akışı Tasarımcısı kullanılır <xref:System.ServiceModel.Activities.Receive> . Daha fazla bilgi için bkz. [etkinlik tasarımcısını alma](../workflow-designer/receive-activity-designer.md).

Etkinlikler arasındaki bağıntı, <xref:System.ServiceModel.Activities.Receive> farklı hizmet işlemlerinin bir iş akışındaki birbirleriyle nasıl bağlanacağını belirtir.

Aşağıdaki tabloda **CorrelatesOn** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|-|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>İletiyi uygun iş akışı örneğine yönlendirmek için kullanılır.|
|**XPath sorguları**|Gelen iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu değer özelliğine karşılık gelir <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> . XPath sorguları bir nesnesi içinde bulunur <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn iletişim kutusunu başlatmak için

**Alma** etkinliği Tasarımcısı **araç kutusu** 'ndan sürüklenebilir ve etkinliklerin genellikle yerleştirildiği her yerde iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, <xref:System.ServiceModel.Activities.Receive> Varsayılan alma için bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . **CorrelatesOn tanımı** iletişim kutusunu açmak için **alma** etkinliği tasarımcısını seçin ve sonra özellik kılavuzunda, **CorrelatesOn** özelliği için koleksiyon metninin yanındaki üç nokta düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializer Ekle İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)