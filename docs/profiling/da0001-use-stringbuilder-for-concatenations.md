---
title: DA0001 - DizeBuilder'ı kullanarak | Microsoft Docs
description: System.String.Concat çağrısı, profil oluşturma verilerinin önemli bir oranıdır. Birden çok segmentten dizeler oluşturmak için System.Text.StringBuilder sınıfını kullanmayı göz önünde bulundurabilirsiniz.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 08edba581d7b88fb0e0a71a7caf99ee66fa0ba3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076743"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Birleştirmeler için StringBuilder kullanma

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0001|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme|
|İleti|Dize concatenations için StringBuilder kullanmayı göz önünde bulundurarak|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 System.String.Concat çağrısı, profil oluşturma verilerinin önemli bir oranıdır. Birden çok <xref:System.Text.StringBuilder> segmentten dizeler oluşturmak için sınıfını kullanmayı göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.String>Bir nesne sabittir. Bu nedenle, dizede yapılan tüm değişiklikler yeni bir dize nesnesi ve özgün dizenin çöp toplaması oluşturur. String.Concat'ı açıkça çağırmanız veya + veya +=.gibi dize concatenation işleçlerini kullanmanız da aynı davranıştır. Bu yöntemler sık çağrılsa(örneğin, dizeye sıkı bir döngüde karakterler ekleniyorsa) program performansı düşebilir.

 StringBuilder sınıfı tarifeli bir nesnedir ve System.String'den farklı olarak, bu sınıfın bir örneğini değiştiren StringBuilder yöntemlerinin çoğu aynı örnek için bir başvuru döndürür. Bir StringBuilder örneğine karakter ekleme veya metin ekleme ve yeni bir örnek ekleme ve özgün örneği silme gerekmeden örnekteki karakterleri kaldırabilir veya değiştirebilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Örnekleme profili verilerine ilişkin İşlev **Ayrıntıları** Görünümüne gitmek için Hata Listesi [penceresindeki](../profiling/function-details-view.md) iletiye çift tıklayın. Programın dize birlemleme en sık kullanılan bölümlerini bulun. Sık sık dize concatenation işlemleri de dahil olmak üzere karmaşık dize işlemeleri için StringBuilder sınıfını kullanın.

 Dizelerle çalışma hakkında daha fazla [](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) bilgi için Microsoft Patterns and Practices kitaplığındaki [Bölüm 5 - Yönetilen](/previous-versions/msp-n-p/ff647790(v=pandp.10)) Kod Performansını Geliştirme bölümünün Dize İşlemleri bölümü.
