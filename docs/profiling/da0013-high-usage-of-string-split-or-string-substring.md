---
title: DA0013 - String.Split veya String.Substring dizelerinin yüksek | Microsoft Docs
description: System.String.Split veya System.String.Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir kısmıdır.
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2502e5021eb0e4e3f3954d068e80819b3034e473
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637158"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0013|
|Kategori|.NET Framework Kullanım Kılavuzu|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|String.Split ve String.Substring işlevlerinin kullanımını azaltmayı göz önünde bulundurabilirsiniz.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 System.String.Split veya System.String.Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir kısmıdır. Bir dizede bir alt dizenin varlığını test ediyorsanız System.String.IndexOfany veya System.String.IndexOfAny kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Split yöntemi bir String nesnesi üzerinde çalışır ve özgün nesnenin alt dizelerini tutan yeni bir Dize dizisi döndürür. İşlev, döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir String nesnesi ayırır. Benzer şekilde, Substr yöntemi bir String nesnesi üzerinde çalışır ve istenen alt dizeye eşdeğer olan yeni bir Dize döndürür.

 Uygulamanıza bellek ayırmalarını yönetmek kritik önem taşıyorsa String.Split ve String.Substr yöntemlerinin alternatiflerini kullanmayı göz önünde bulundurabilirsiniz. Örneğin, String sınıfının yeni bir örneğini oluşturmadan bir karakter Dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanabilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Hata Listesi penceresindeki iletiyi **çift** tıklatın ve örnekleme profili [verilerine ilişkin İşlev](../profiling/function-details-view.md) Ayrıntıları Görünümüne gidin. Programın System.String.Split veya System.String.Substr yöntemlerini en sık kullanan bölümlerini bulmak için çağrı işlevlerini inceler. Mümkünse, String sınıfının yeni bir örneğini oluşturmadan bir karakter Dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanın.
