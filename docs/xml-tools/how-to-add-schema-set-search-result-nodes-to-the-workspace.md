---
title: Şema kümesi arama sonucu düğümleri Ekle
description: Çalışma alanında bir anahtar sözcük aramasının sonucu olarak XML şema Gezgini 'nde vurgulanan düğümleri nasıl ekleyeceğinizi öğrenin.
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
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Nasıl yapılır: şema kümesi arama sonucu düğümlerini çalışma alanına ekleme

Bu konu, çalışma alanında bir anahtar sözcük aramasının sonucu olarak **XML şema Gezgini** 'nde vurgulanan düğümlerin nasıl ekleneceğini açıklar.

> [!NOTE]
> [Çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)yalnızca genel düğümler eklenebilir.

Bu örnek, örnek [satın alma siparişi şemasını](../xml-tools/sample-xsd-file-purchase-order-schema.md)kullanır.

## <a name="to-add-schema-set-result-nodes"></a>Şema kümesi sonuç düğümleri eklemek için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "PurchaseOrder" yazın ve arama düğmesine tıklayın.

     ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif)

     Arama sonuçları, **XML şema Gezgini** 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir.

3. Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyin.

     ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`düğüm ve düğüm, `PurchaseOrderType` [Graph görünümünün](../xml-tools/graph-view.md)tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan ( `purchaseOrder` öğe `PurchaseOrderType` türünde olduğundan) aralarında bir ok çizilir.
