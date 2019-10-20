---
title: Şema kümesi aranıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656166"
---
# <a name="searching-the-schema-set"></a>Şema Kümesini Arama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML şeması Gezgini şema kümesini aşağıdaki yollarla aramanızı sağlar:

- Anahtar sözcük arama.

- Şemaya özgü arama.

## <a name="keyword-search"></a>Anahtar sözcük arama
 XML şeması Gezgini araç çubuğunun **arama şeması kümesi** metin kutusuna bir alt dize girerek anahtar sözcük aramaları gerçekleştirirsiniz.

 ![XML şema Gezgini anahtar sözcük arama](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 XML şeması Gezgini şema kümesini Aşağıdakiler için arar:

- Belirtilen anahtar sözcükle eşleşen herhangi bir `name` veya `ref` özniteliği. Bu, öğeleri, öznitelikleri, türleri ve diğer adı adına göre bulmanızı sağlar.

- Include deyimlerinin `schemaLocation` öznitelikleri.

- İmport deyimlerinin `namespace` öznitelikleri.

## <a name="schema-specific-search"></a>Şemaya özgü arama
 XML şeması Gezgini, XML şema Gezgini 'nin bağlam menüsünü kullanarak erişebileceğiniz yerleşik aramalar da içerir. Kullanılabilir bağlam menüleri hakkında daha fazla bilgi için bkz. [Bağlam menüleri](../xml-tools/context-menus-xml-schema-explorer.md). Ayrıca, başlangıç görünümünden şemaya özgü bir arama da yapabilirsiniz; daha fazla bilgi için [Başlangıç görünümü](../xml-tools/start-view.md) konusunun "şema kümesi ayrıntıları" bölümüne bakın.

## <a name="displaying-and-navigating-search-results"></a>Arama sonuçlarını görüntüleme ve gezinme
 Arama tamamlandıktan sonra, özet sonuçları bölmesi, arama sonuçlarıyla birlikte araç çubuğuna eklenir. Arama sonuçları ayrıca XML şema Gezgini 'nde vurgulanır ve dikey kaydırma çubuğundaki Tick 'ler tarafından işaretlenir. Arama sonuçlarında, **sonraki arama sonuçlarına git** ' i kullanarak ve XML şeması Gezgini araç çubuğunun özet sonuçları bölmesinde **önceki arama sonucu düğmesine gidebilirsiniz** ; F3 ve SHIFT + F3 klavye tuşlarını kullanarak ya da kaydırma çubuğundaki onay işaretlerine tıklayarak.

 Özet sonuçlar bölmesinde, **çalışma alanına vurgulanan düğümleri Ekle** düğmesine tıklayarak arama sonuçlarını çalışma alanına ekleyebilirsiniz.

 ![XML şema Gezgini arama sonucu](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Arama sonuçlarını Temizleme
 Arama sonuçlarını temizlemek için, XML şeması Gezgini arama araç çubuğunun özet sonuçlar bölmesindeki **x** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
