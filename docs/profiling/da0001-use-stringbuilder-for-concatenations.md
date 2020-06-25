---
title: DA0001-birleştirmeleri için StringBuilder kullan | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 137d21019973ac78a74429e957429d69d91edbf8
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332111"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Birleştirmeler için StringBuilder kullanma

|||
|-|-|
|Kural kimliği|DA0001|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme|
|İleti|Dize birleştirmeleri için StringBuilder kullanmayı düşünün|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 System. String. Concat çağrısı, profil oluşturma verilerinin önemli bir orandır. <xref:System.Text.StringBuilder>Birden çok kesimden dizeler oluşturmak için sınıfını kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Bir <xref:System.String> nesne sabittir. Bu nedenle, dizedeki tüm değişiklikler yeni bir dize nesnesi ve özgün bir çöp toplama oluşturur. Bu davranış, String. Concat öğesini açık bir şekilde çağırıp veya + ya da + = gibi dize birleştirme işleçlerini kullanın. Bu yöntemler sık sık çağrılırsa (örneğin, sıkı bir döngüde bir dizeye karakterler eklendiğinde) program performansı azalabilir.

 StringBuilder sınıfı kesilebilir bir nesnedir ve System. String 'ten farklı olarak, bu sınıfın bir örneğini değiştiren StringBuilder üzerindeki yöntemlerin çoğu aynı örneğe bir başvuru döndürür. Bir StringBuilder örneğine karakter ekleyebilir veya metin ekleyebilir ve yeni bir örnek ayırma ve özgün örneği silme gereksinimi olmadan örnekteki karakterleri kaldırabilir veya değiştirebilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Örnekleme profili verilerinin [Işlev ayrıntıları görünümüne](../profiling/function-details-view.md) gitmek için **hata listesi** penceresindeki iletiye çift tıklayın. Dize bitişinin en sık kullanımını yapan programın bölümlerini bulun. Sık kullanılan dize birleştirme işlemleri dahil olmak üzere karmaşık dize düzenlemeleri için StringBuilder sınıfını kullanın.

 Dizeler ile çalışma hakkında daha fazla bilgi için, Microsoft desenleri ve uygulamalar kitaplığındaki [yönetilen kod performansını artırma başlıklı Bölüm 5](/previous-versions/msp-n-p/ff647790(v=pandp.10)) ' ın [dize işlemleri](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) bölümü.
