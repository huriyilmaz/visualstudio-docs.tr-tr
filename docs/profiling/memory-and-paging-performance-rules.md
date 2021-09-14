---
title: Bellek ve disk belleği performans kuralları | Microsoft Docs
description: Bellek ve disk belleği kategorisindeki performans kurallarının, uygulama performansını ve yanıt hızını etkileyebilecek bir profil oluşturma çalıştırmasında sayfalama etkinliğini nasıl tanımlacağınızı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628347"
---
# <a name="memory-and-paging-performance-rules"></a>Bellek ve disk belleği performans kuralları
Bellek ve disk belleği kategorisindeki performans kuralları, uygulama performansını ve yanıt hızını etkileyebilecek bir profil oluşturma çalıştırmasında sayfalama etkinliğini belirler.

|Kural|Description|
|-|-|
|[DA0014: Çok yüksek oranda diske etkin bellek sayfalaması](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırmasının tamamında son derece yüksek oranda disk belleğine ve diske etkin bellek sayfalaması gerçekleşti. Bu düzeydeki disk belleği ücretleri genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaların yeniden gözden geçirerek bellek ayırmalarını azaltmayı göz önünde bulundurun. Ayrıca, uygulamanızın bellek gereksinimlerini dikkate almanız gerekebilir. Daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin. Bu kural, sayfalama etkinliğinin miktarı D0017 kural üst eşiğini aştığında ateşlenir.|
|[DA0017: Yüksek oranda diske etkin bellek sayfalaması](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalıştırmasının tamamında, disk üzerinde ve diskten etkin belleği olan yüksek oranda disk belleği miktarı. Bu düzeydeki disk belleği ücretleri genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaların yeniden gözden geçirerek bellek ayırmalarını azaltmayı göz önünde bulundurun. Ayrıca, uygulamanızın bellek gereksinimlerini dikkate almanız gerekebilir. Daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin.|
