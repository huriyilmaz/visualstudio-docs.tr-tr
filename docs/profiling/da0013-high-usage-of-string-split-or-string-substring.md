---
title: DA0013-en yüksek dize. Split veya String. Substring kullanımı | Microsoft Docs
description: System. String. Split veya System. String. Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir bölümüdür.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142292"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0013|
|Kategori|.NET Framework Kullanım Kılavuzu|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|String. Split ve String. SUBSTRING işlevlerinin kullanımını azaltmayı göz önünde bulundurun.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 System. String. Split veya System. String. Substring yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir bölümüdür. Bir dizedeki alt dizenin varlığını test ediyorsanız System. String. IndexOf veya System. String. IndexOfAny kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Split yöntemi bir dize nesnesi üzerinde çalışır ve özgün dizenin alt dizelerini tutan yeni bir dize dizisi döndürür. İşlevi döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir dize nesnesi ayırır. Benzer şekilde, substr Yöntemi bir String nesnesi üzerinde çalışır ve istenen alt dizeyle eşdeğer olan yeni bir dize döndürür.

 Uygulamanızda bellek ayırmaları yönetimi önemliyse, String. Split ve String. substr yöntemlerine alternatifleri kullanmayı göz önünde bulundurun. Örneğin, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanabilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Örnekleme profili verilerinin [Işlev ayrıntıları görünümüne](../profiling/function-details-view.md) gitmek için **hata listesi** penceresindeki iletiye çift tıklayın. System. String. Split veya System. String. substr yöntemlerinin en sık kullanımını yapan programın bölümlerini bulmak için çağırma işlevlerini inceleyin. Mümkünse, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemini kullanın.
