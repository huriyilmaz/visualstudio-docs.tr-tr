---
title: 'Nasıl yapılır: şema kümesi arama sonucu düğümlerini çalışma alanına ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666545"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Nasıl Yapılır: Şema Kümesi Arama Sonucu Düğümlerini Çalışma Alanına Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, çalışma alanında bir anahtar sözcük aramasının sonucu olarak XML şema Gezgini 'nde vurgulanan düğümlerin nasıl ekleneceğini açıklar.

> [!NOTE]
> [Çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)yalnızca genel düğümler eklenebilir.

 Bu örnek, örnek [satın alma siparişi şemasını](../xml-tools/sample-xsd-file-purchase-order-schema.md)kullanır.

### <a name="to-add-schema-set-result-nodes"></a>Şema kümesi sonuç düğümleri eklemek için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML Explorer](../xml-tools/xml-schema-explorer.md) araç çubuğunun arama metin kutusuna "PurchaseOrder" yazın ve arama düğmesine tıklayın.

     ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Arama sonuçları, XML şema Gezgini 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir.

3. Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyin.

     ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder`Düğüm ve düğüm, `PurchaseOrderType` [Grafik görünümünün](../xml-tools/graph-view.md)tasarım yüzeyinde birbirini izleyen bir şekilde görünür. İki düğüm ilişkili olduğundan ( `purchaseOrder` öğe `PurchaseOrderType` türünde olduğundan) aralarında bir ok çizilir.
