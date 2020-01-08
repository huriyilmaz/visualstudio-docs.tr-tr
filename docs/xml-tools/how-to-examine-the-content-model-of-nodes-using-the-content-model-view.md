---
title: XML şema tasarımcısında Içerik modeli görünümünü kullanarak düğümleri inceleyin
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592717"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Nasıl yapılır: Içerik modeli görünümünü kullanarak düğümlerin içerik modelini Inceleme

Bu konu, [Içerik modeli görünümünü](../xml-tools/content-model-view.md)kullanarak düğümlerinizi nasıl keşfedebileceğinizi açıklamaktadır.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyasını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [örnek xml şemasından kopyalayın: satın alma sırası şeması](../xml-tools/sample-xsd-file-purchase-order-schema.md) , varsayılan olarak yeni xsd dosyasına eklenen kodu değiştirmek için yapıştırın.

4. XML düzenleyicisinde `purchaseOrder` öğesine sağ tıklayıp **XML Explorer 'Da göster '** i seçerek şema Gezgininde `purchaseOrder` öğesini seçin.

5. XML Explorer 'da `purchaseOrder` sağ tıklayın ve **Içerik modeli görünümünde göster**' i seçin.

     Içerik modeli görünümü `purchaseOrder` öğesini tasarım yüzeyinde görüntüler.

6. Her bir düğüme çift tıklayarak veya her bir düğümün sağ tarafındaki çift oka tıklayarak `shipTo`, `billTo`ve `items` düğümlerini genişletin.

     `purchaseOrder` öğenin düğümleri artık genişletilir ve öğenin içerik modelini görebilirsiniz.

7. `purchaseOrder` öğesinin altındaki herhangi bir düğüme tıklayın ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Belge değiştirmek için XSD araç çubuğundaki **belgeleri göster** düğmesine tıklayın. Ayrıca, belge değiştirmek için tasarım yüzeyine sağ tıklayabilirsiniz.

9. `purchaseOrder` düğümüne sağ tıklayıp XML örnek belgesini görmek için **örnek XML oluştur** ' u seçin.
