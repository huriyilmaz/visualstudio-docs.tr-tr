---
title: XML şema Gezgini 'nden çalışma alanına düğüm ekleme
description: Bağlam menüsünü kullanarak veya düğümleri bir görünüm üzerine sürükleyip bırakarak XML şema Tasarımcısı çalışma alanına düğüm ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 4c55f920d07d2f6230022d78a2a98b77cb86ebd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045599"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Nasıl yapılır: XML şema Gezgini 'nden çalışma alanına düğüm ekleme

Bu konu başlığı altında, XML şema **Gezgini**' nden [XML şema Tasarımcısı çalışma alanına](../xml-tools/xml-schema-designer-workspace.md) düğümlerin nasıl ekleneceği açıklanmaktadır. Bu, düğümleri **XML şema** Gezgininden bir xsd tasarımcı görünümüne sürükleyip bırakarak veya **XML şeması Gezgini 'nin** bağlam menüsünü kullanarak elde edilebilir. Ayrıca, **XML şema Gezgini** tarafından gerçekleştirilen bir aramanın sonucu olarak vurgulanan düğümleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: şema kümesi arama sonucu düğümlerini çalışma alanına ekleme](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> [XML şema Tasarımcısı çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)yalnızca genel düğümler eklenebilir.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML Gezgini bağlam menüsü aracılığıyla düğüm eklemek için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. `PurchaseOrderType`XSD Explorer 'da düğüme sağ tıklayın. **Graph görünümünde göster '** i seçin.

     `purchaseOrderType`düğüm, Graph görünümünün tasarım yüzeyinde görünür.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Bir düğümü bir görünüme sürükleyip bırakmak için

1. `PurchaseOrderType`Graph görünümündeki düğüme sağ tıklayın. **XML şema Gezgininde Göster '** i seçin.

     Düğüm, **XML şema Gezgini**'nde vurgulanır.

2. `PurchaseOrderType` **XML şema Gezgini** ' nde düğüme sağ tıklayın ve **tüm başvuruları göster**' i seçin.

     `purchaseOrder`Düğüm vurgulanır.

3. `purchaseOrder`düğümü Graph görünümüne sürükleyin.

     `purchaseOrder`düğüm ve düğüm, `PurchaseOrderType` Graph görünümünün tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan ( `purchaseOrder` öğe `PurchaseOrderType` türünde olduğundan) aralarında bir ok çizilir.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Şema Gezgini arama özelliğini kullanarak düğüm eklemek için

1. [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "PurchaseOrder" yazın ve arama düğmesine tıklayın.

     ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif)

     Arama sonuçları, **XML şema Gezgini** 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir.

2. Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyin.

     ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`düğüm ve düğüm, `PurchaseOrderType` [Graph görünümünün](../xml-tools/graph-view.md)tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan ( `purchaseOrder` öğe `PurchaseOrderType` türünde olduğundan) aralarında bir ok çizilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
