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
ms.openlocfilehash: 7e8606ea4d44d374a6d0c8b59905038b352aceaa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054632"
---
# <a name="memory-and-paging-performance-rules"></a>Bellek ve disk belleği performans kuralları
Bellek ve disk belleği kategorisindeki performans kuralları, profil oluşturma çalıştırması içinde uygulama performansını ve yanıt hızını etkileyebilirsiniz.

|Kural|Açıklama|
|-|-|
|[DA0014: Çok yüksek oranda diske etkin bellek sayfalaması](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırması boyunca diske gelen ve diskten etkin bellek diske gelen disk belleğinin son derece yüksek bir oranı oluştu. Bu düzeydeki disk belleği hızları genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz. Daha fazla belleği olan bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin. Bu kural, disk belleği etkinliği miktarı D0017 kuralının üst eşiğini aştı mı?|
|[DA0017: Yüksek oranda diske etkin bellek sayfalaması](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırması boyunca diske gelen ve diskten etkin bellek diske görece yüksek disk belleği oranı oluştu. Bu düzeydeki disk belleği hızları genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz. Daha fazla belleği olan bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin.|
