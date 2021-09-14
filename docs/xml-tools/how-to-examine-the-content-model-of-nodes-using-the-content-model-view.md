---
title: Düğümlerin içerik modelini inceleme
description: XML şemasında düğümlerin içerik modelini incelemek için XML Şema Tasarımcısı'nda İçerik Modeli Görünümünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: a9e1b5d1ebd573f74762d86717118138adea23d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633622"
---
# <a name="how-to-examine-the-content-model-of-nodes-by-using-the-content-model-view"></a>Nasıllı: İçerik Modeli Görünümünü kullanarak düğümlerin içerik modelini inceleme

Bu konu başlığında, İçerik Modeli Görünümü'ünü kullanarak [düğümlerinizi nasıl keşfedebilirsiniz?](../xml-tools/content-model-view.md)

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve kök öğeyi İçerik Modeli Görünümünde görüntülemek için

1. Yeni bir XML Şema dosyası oluşturun.

2. Başlangıç **Görünümünde temel XML Şeması dosyasını görüntülemek ve düzenlemek için XML düzenleyicisini** kullan'a tıklayın.

3. Örnek XML şeması: satın alma siparişi şemasından [XML](../xml-tools/sample-xsd-file-purchase-order-schema.md) Şeması örnek kodunu kopyalayın ve varsayılan olarak yeni XSD dosyasına eklenen kodu değiştirmek için yapıştırın.

4. XML `purchaseOrder` düzenleyicisinde öğesine sağ tıklar ve `purchaseOrder` XML Gezgini'nde Göster'i seçerek Şema **Gezgini'nde öğesini seçin.**

5. XML Gezgini'nde `purchaseOrder` dosyasına sağ tıklayın ve İçerik Modeli Görünümünde **Göster'i seçin.**

     İçerik Modeli Görünümü, öğeyi `purchaseOrder` tasarım yüzeyinde görüntüler.

6. Her düğüme çift tıklayarak veya her düğümün sağ yanındaki çift oka tıklayarak , ve `shipTo` `billTo` `items` düğümlerini genişletin.

     Öğesinin düğümleri `purchaseOrder` artık genişletildi ve öğenin içerik modelini görüyorsunuz.

7. öğesinin altındaki herhangi bir düğüme tıklayın ve seçilen düğümün şema kümesinde nerede olduğunu görmek `purchaseOrder` için breadcrumb çubuğuna bakın.

8. Belgeleri değiştirmek **için** XSD Araç Çubuğunda Belgeleri Göster düğmesine tıklayın. Ayrıca, belgeleri değiştirmek için tasarım yüzeyine sağ tıkabilirsiniz.

9. Düğüme sağ tıklayın `purchaseOrder` ve XML örneği belgesini görmek için Örnek **XML** Oluştur'u seçin.
