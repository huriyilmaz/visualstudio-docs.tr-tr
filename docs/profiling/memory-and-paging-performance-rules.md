---
title: Bellek ve Sayfalama Performans Kuralları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f491ee766b2f17e14a8d13cc189018adea84903f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778563"
---
# <a name="memory-and-paging-performance-rules"></a>Bellek ve sayfalama performans kuralları
Bellek ve sayfalama kategorisindeki performans kuralları, uygulama performansını ve yanıt verme yeteneğini etkilenebilen bir profil oluşturma çalışmasında sayfalama etkinliğini tanımlar.

|||
|-|-|
|[DA0014: Aşırı yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalışması boyunca diske ve diskten gelen son derece yüksek bir sayfalama oranı oluştu. Bu düzeydeki sayfalama oranları genellikle uygulama performansını ve yanıt verme yeteneğini etkiler. Algoritmaları gözden geçirerek bellek ayırmalarını azaltmayı düşünün. Uygulamanızın bellek gereksinimlerini de göz önünde bulundurmanız gerekebilir. Daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin. Bu kural, sayfalama etkinliği miktarı D0017 kuralının üst eşiğini aştığında yangınlar.|
|[DA0017: Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Profil oluşturma çalışması boyunca diske ve diskten gelen etkin bellek tevekresiler nispeten yüksek bir hız oluştu. Bu düzeydeki sayfalama oranları genellikle uygulama performansını ve yanıt verme yeteneğini etkiler. Algoritmaları gözden geçirerek bellek ayırmalarını azaltmayı düşünün. Uygulamanızın bellek gereksinimlerini de göz önünde bulundurmanız gerekebilir. Daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırmayı deneyin.|
