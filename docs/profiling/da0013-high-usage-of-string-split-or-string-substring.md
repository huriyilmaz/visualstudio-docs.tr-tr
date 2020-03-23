---
title: 'DA0013: String.Split veya String.Substring yüksek kullanımı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d42469ac5236a41eda96af5d1fe896a5ed84a321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779419"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı

|||
|-|-|
|Kural Id|DA0013|
|Kategori|.NET Çerçeve Kullanım Kılavuzu|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|String.Split ve String.Substring işlevlerinin kullanımını azaltmayı düşünün.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 System.String.Split veya System.String.Substring yöntemlerine yapılan çağrılar profil oluşturma verilerinin önemli bir bölümütür. Bir dize bir substring varlığını test ediyorsanız System.String.IndexOf veya System.String.IndexOfAny kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Split yöntemi Bir String nesnesi üzerinde çalışır ve özgün alt dizeleri tutan dizeleri yeni bir dizi döndürür. İşlev, döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir String nesnesi ayırır. Benzer şekilde, Substr yöntemi bir String nesnesi üzerinde çalışır ve istenen substring eşdeğer yeni bir String döndürür.

 Uygulamanızda bellek ayırmalarını yönetmek çok önemliyse, String.Split ve String.Substr yöntemlerine alternatifler kullanmayı düşünün. Örneğin, String sınıfının yeni bir örneğini oluşturmadan bir karakter String içinde belirli bir alt dize bulmak için IndexOf veya IndexOfAny yöntemini kullanabilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Örnekleme profili verilerinin [İşlev Ayrıntıları Görünümü'ne](../profiling/function-details-view.md) gitmek için **Hata Listesi** penceresindeki iletiyi çift tıklatın. System.String.Split veya System.String.Substr yöntemlerini en sık kullanan bölümü bulmak için arama işlevlerini inceleyin. Mümkünse, String sınıfının yeni bir örneğini oluşturmadan string içinde belirli bir alt dize bulmak için IndexOf veya IndexOfAny yöntemini kullanın.
