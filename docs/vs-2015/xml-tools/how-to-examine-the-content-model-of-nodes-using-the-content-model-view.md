---
title: 'Nasıl Yapılır: Içerik modeli görünümünü kullanarak düğümlerin Içerik modelini inceleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670854"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Nasıl Yapılır: İçerik Modeli Görünümünü Kullanarak Düğümlerin İçerik Modelini İnceleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, [Içerik modeli görünümünü](../xml-tools/content-model-view.md)kullanarak düğümlerinizi nasıl keşfedebileceğinizi açıklamaktadır.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyasını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [Sample XML şemasından kopyalayın: Satın alma siparişi şeması ](../xml-tools/sample-xsd-file-purchase-order-schema.md) ve yeni XSD dosyasına eklenen kodu varsayılan olarak değiştirmek için yapıştırın.

4. XML düzenleyicisinde `purchaseOrder` öğesine sağ tıklayıp **XML Explorer 'Da göster '** i seçerek şema Gezgininde `purchaseOrder` öğesini seçin.

5. XML Explorer 'da `purchaseOrder` sağ tıklayın ve **Içerik modeli görünümünde göster**' i seçin.

     Içerik modeli görünümü `purchaseOrder` öğesini tasarım yüzeyinde görüntüler.

6. Her bir düğüme çift tıklayarak veya her bir düğümün sağ tarafındaki çift oka tıklayarak `shipTo`, `billTo` ve `items` düğümlerini genişletin.

     @No__t_0 öğenin düğümleri artık genişletilir ve öğenin içerik modelini görebilirsiniz.

7. @No__t_0 öğesinin altındaki herhangi bir düğüme tıklayın ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Belge belgelerini değiştirmek için XSD araç çubuğundaki **belgeleri göster** düğmesine tıklayın. Ayrıca, belge değiştirmek için tasarım yüzeyine sağ tıklayabilirsiniz.

9. Rick-`purchaseOrder` düğümüne tıklayıp XML örnek belgesini görmek için **örnek XML oluştur** ' u seçin.
