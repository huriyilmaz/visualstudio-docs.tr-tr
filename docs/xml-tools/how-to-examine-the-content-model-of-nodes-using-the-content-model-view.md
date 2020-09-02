---
title: XML şema tasarımcısında Içerik modeli görünümünü kullanarak düğümleri inceleyin
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bf6294aeac9a23168bf9cf9aaec26efbfc6c1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815987"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Nasıl yapılır: Içerik modeli görünümünü kullanarak düğümlerin içerik modelini Inceleme

Bu konu, [Içerik modeli görünümünü](../xml-tools/content-model-view.md)kullanarak düğümlerinizi nasıl keşfedebileceğinizi açıklamaktadır.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyasını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [örnek xml şemasından kopyalayın: satın alma sırası şeması](../xml-tools/sample-xsd-file-purchase-order-schema.md) , varsayılan olarak yeni xsd dosyasına eklenen kodu değiştirmek için yapıştırın.

4. `purchaseOrder` `purchaseOrder` XML düzenleyicisinde öğesine sağ tıklayıp **XML Explorer 'da göster**' i seçerek şema Gezgini ' nde öğesini seçin.

5. `purchaseOrder`XML Explorer 'da öğesine sağ tıklayın ve **Içerik modeli görünümünde göster**' i seçin.

     Içerik modeli görünümü, `purchaseOrder` öğesini tasarım yüzeyinde görüntüler.

6. Her bir `shipTo` `billTo` `items` düğüme çift tıklayarak veya her bir düğümün sağ tarafındaki çift oka tıklayarak,, ve düğümlerini genişletin.

     `purchaseOrder`Öğenin düğümleri artık genişletilir ve öğenin içerik modelini görebilirsiniz.

7. Öğesinin altındaki herhangi bir düğüme tıklayın `purchaseOrder` ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Belge değiştirmek için XSD araç çubuğundaki **belgeleri göster** düğmesine tıklayın. Ayrıca, belge değiştirmek için tasarım yüzeyine sağ tıklayabilirsiniz.

9. `purchaseOrder`XML örnek belgesini görmek için düğüme sağ tıklayın ve **örnek XML oluştur** ' u seçin.
