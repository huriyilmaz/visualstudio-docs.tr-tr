---
title: 'Nasıl yapılır: Içerik modeli görünümünü kullanarak düğümlerin Içerik modelini Inceleme | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670854"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Nasıl Yapılır: İçerik Modeli Görünümünü Kullanarak Düğümlerin İçerik Modelini İnceleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, [Içerik modeli görünümünü](../xml-tools/content-model-view.md)kullanarak düğümlerinizi nasıl keşfedebileceğinizi açıklamaktadır.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Yeni bir XSD dosyası oluşturmak ve Içerik modeli görünümünde kök öğeyi görüntülemek için

1. Yeni bir XML şema dosyası oluşturun.

2. Başlangıç görünümündeki **temel ALıNAN XML şema dosyasını görüntülemek ve düzenlemek IÇIN XML düzenleyicisini kullan** ' a tıklayın.

3. XML şeması örnek kodunu [örnek xml şemasından kopyalayın: satın alma sırası şeması](../xml-tools/sample-xsd-file-purchase-order-schema.md) , varsayılan olarak yeni xsd dosyasına eklenen kodu değiştirmek için yapıştırın.

4. `purchaseOrder` `purchaseOrder` XML düzenleyicisinde öğesine sağ tıklayıp **XML Explorer 'da göster**' i seçerek şema Gezgini ' nde öğesini seçin.

5. `purchaseOrder`XML Explorer 'da öğesine sağ tıklayın ve **Içerik modeli görünümünde göster**' i seçin.

     Içerik modeli görünümü, `purchaseOrder` öğesini tasarım yüzeyinde görüntüler.

6. Her bir `shipTo` `billTo` `items` düğüme çift tıklayarak veya her bir düğümün sağ tarafındaki çift oka tıklayarak,, ve düğümlerini genişletin.

     `purchaseOrder`Öğenin düğümleri artık genişletilir ve öğenin içerik modelini görebilirsiniz.

7. Öğesinin altındaki herhangi bir düğüme tıklayın `purchaseOrder` ve seçili düğümün şema kümesinde nerede olduğunu görmek için içerik haritası çubuğuna bakın.

8. Belge belgelerini değiştirmek için XSD araç çubuğundaki **belgeleri göster** düğmesine tıklayın. Ayrıca, belge değiştirmek için tasarım yüzeyine sağ tıklayabilirsiniz.

9. Rick-düğümü tıklatın `purchaseOrder` ve XML örnek belgesini görmek Için **örnek XML oluştur** ' u seçin.
