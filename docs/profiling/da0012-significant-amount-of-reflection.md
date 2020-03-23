---
title: 'DA0012: Yansıma önemli miktarda | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1c1b96e9a73b488ba9c9920e8ea43e27f78f67ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777679"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Önemli miktarda Yansıma

|||
|-|-|
|Kural Id|DA0012|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Yansıma'yı aşırı kullanıyor olabilirsiniz. Pahalı bir operasyon.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 InvokeMember ve GetMember gibi System.Reflection yöntemlerine veya MemberInvoke gibi yazı yöntemlerine yapılan çağrılar profil oluşturma verilerinin önemli bir kısmıdır. Mümkün olduğunda, bağımlı derlemelerin yöntemlerine erken bağlama ile bu yöntemleri değiştirmeyi düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Yansıma, .NET Framework'ün, uygulamanızın bağımlı çalışma zamanı Derlemesine geç bağlanmasını gerçekleştirmek veya çalışma süresi sırasında yeni türler oluşturmak ve dinamik olarak yürütmek için kullanılabilecek esnek bir tesistir. Ancak, bu teknikler sık kullanılırsa veya sıkı döngüler halinde çağrılırsa performansı azaltabilir.

 Daha fazla bilgi için, BÖLÜM 5'in Yansıma ve Geç Bağlama bölümüne bakın — MSDN'deki Microsoft [Desenleri ve](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) Uygulamaları kitaplığının .NET Uygulama Performansını ve Ölçeklenebilirlik düzeyini Artırmada Yönetilen Kod Performansını İyileştirme bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [İşlev Ayrıntıları Görünümü'ne](../profiling/function-details-view.md) gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. .NET Yansıma API'lerini en sık kullanan bölümü bulmak için System.Type veya System.Reflection yönteminin arama işlevlerini inceleyin. Meta verileri döndüren yöntemler kullanmaktan kaçının. Uygulamanızın performansı kritik olduğunda, çalışma zamanında geç bağlama ve dinamik türler oluşturmaktan kaçınmanız gerekebilir.
