---
title: Bellek ve Disk Belleği Performans Kuralları | Microsoft Docs
description: Bellek ve disk belleği kategorisindeki performans kurallarının, profil oluşturma çalıştırması içinde uygulama performansını ve yanıt hızını etkileyene disk belleği etkinliğini nasıl tanımlay olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 71697bcfd375217ca54be591ec18b334369853b0e1a71bccb5aa2bdb27a41058
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410481"
---
# <a name="memory-and-paging-performance-rules"></a>Bellek ve disk belleği performans kuralları
Bellek ve disk belleği kategorisindeki performans kuralları, profil oluşturma çalıştırması içinde uygulama performansını ve yanıt hızını etkileyebilirsiniz.

|Kural|Açıklama|
|-|-|
|[DA0014: Çok yüksek oranda diske etkin bellek sayfalaması](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırması boyunca diske gelen ve diskten etkin bellek diske gelen disk belleğinin son derece yüksek bir oranı oluştu. Bu düzeydeki disk belleği hızları genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz. Daha fazla belleği olan bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin. Bu kural, disk belleği etkinliği miktarı D0017 kuralının üst eşiğini aştı mı?|
|[DA0017: Yüksek oranda diske etkin bellek sayfalaması](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırması boyunca diske gelen ve diskten etkin bellek diske görece yüksek disk belleği oranı oluştu. Bu düzeydeki disk belleği hızları genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz. Daha fazla belleği olan bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin.|
