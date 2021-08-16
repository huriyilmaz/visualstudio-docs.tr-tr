---
title: Şema kümesi arama sonucu düğümleri ekleme
description: Çalışma alanında anahtar sözcük araması sonucunda XML Şema Gezgini'nde vurgulanan düğümleri nasıl ekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: e9ab42d35aef489c18a12c3c738655dde1ccb9e971bf0caaf87513582645a79f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351011"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Nasıl olur: Çalışma alanına şema kümesi arama sonucu düğümleri ekleme

Bu konuda, çalışma alanında anahtar sözcük araması sonucu **XML Şema Gezgini'nde** vurgulanan düğümlerin nasıl ekli olduğu açıklanmıştır.

> [!NOTE]
> Çalışma alanına yalnızca genel düğümler [eklenebilir.](../xml-tools/xml-schema-designer-workspace.md)

Bu örnek, örnek satın [alma siparişi şemasını kullanır.](../xml-tools/sample-xsd-file-purchase-order-schema.md)

## <a name="to-add-schema-set-result-nodes"></a>Şema kümesi sonuç düğümleri eklemek için

1. Nasıl olur: [XSD şema dosyası oluşturma ve düzenleme adımlarını izleyin.](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)

2. [XML Gezgini](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "purchaseOrder" yazın ve ara düğmesine tıklayın.

     ![XML Şema Gezgini Anahtar Sözcük Arama](../xml-tools/media/schemaexplorersearch.gif)

     Arama sonuçları XML Şema Gezgini'nde **vurgulanır** ve dikey kaydırma çubuğunda tıklar ile işaretlenir.

3. Özet sonuçları bölmesindeki Vurgulanan düğümleri Çalışma Alanına ekle **düğmesine tıklayarak** arama sonuçlarını çalışma alanına ekleyin.

     ![XML Şema Gezgini Arama Sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     Düğüm `purchaseOrder` ve `PurchaseOrderType` düğüm, görünüm görünümü'nin tasarım yüzeyinde Graph [görünür.](../xml-tools/graph-view.md) İki düğüm ilişkili olduğundan (öğe `purchaseOrder` `PurchaseOrderType` türündedir), aralarında bir ok çizilir.
