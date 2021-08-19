---
title: İş Akışı Tasarımcısı - CorrelatesOn Tanımı İletişim Kutusu
description: Bir Receive etkinliğinin CorrelatesOn özelliğini düzenlemek için İş Akışı Tasarımcısı iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 0b0730853bb2f7e67445a85c4a05d6adbfc22dc3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155271"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn Tanımı İletişim Kutusu

**CorrelatesOn** iletişim kutusu, İş Akışı Tasarımcısı özelliğini düzenlemek <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> için bu iletişim kutusunda <xref:System.ServiceModel.Activities.Receive> kullanılır. Daha fazla bilgi için bkz. [Alma Etkinlik Tasarımcısı.](../workflow-designer/receive-activity-designer.md)

Etkinlikler arasındaki <xref:System.ServiceModel.Activities.Receive> bağıntı, farklı hizmet işlemlerinin bir iş akışında birbirine nasıl bağlanıyor olduğunu belirtir.

Aşağıdaki **tablo, CorrelatesOn** iletişim kutusunun kullanıcı arabirimi (UI) öğelerini açıklar.

|Arabirim Öğesi|Açıklama|
|-|-----------------|
|**CorrelatesWith**|İletiyi <xref:System.ServiceModel.Activities.CorrelationHandle> uygun iş akışı örneğine yönlendirmek için kullanılan.|
|**XPath Sorguları**|Gelen iletilerden bağıntı verilerini ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu değer özelliğine <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> karşılık gelen değerdir. XPath sorguları bir nesnesinde <xref:System.ServiceModel.MessageQuerySet> yer almaktadır.|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn iletişim kutusunu başlatmak için

Alma  etkinliği tasarımcısı, etkinlikler genellikle **yerleştirildikten** sonra Araç Kutusundan sürükleyip İş Akışı Tasarımcısı yüzeyine bırakılır. Etkinlik tasarımcısını bırakarak varsayılan <xref:System.ServiceModel.Activities.Receive> Alma değerine sahip bir <xref:System.Activities.Activity.DisplayName%2A> etkinlik oluşturur. **CorrelatesOn Tanımı** iletişim kutusunu açmak  için Alma etkinliği tasarımcısını seçin ve ardından özellik kılavuzunda **CorrelatesOn** özelliğinin Koleksiyon metninin yanındaki üç nokta düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializer Ekle İletişim Kutusu](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)