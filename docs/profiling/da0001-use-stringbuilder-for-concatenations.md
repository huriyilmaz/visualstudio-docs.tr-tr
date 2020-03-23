---
title: 'DA0001: Concatenations için StringBuilder kullanın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 0d93de6ce901bfe4d72628f778b18420beb5ebee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779512"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Birleştirmeler için StringBuilder kullanın

|||
|-|-|
|Kural Id|DA0001|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme|
|İleti|String concatenations için StringBuilder kullanmayı düşünün|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 System.String.Concat'e yapılan aramalar profil oluşturma verilerinin önemli bir kısmıdır. Birden çok <xref:System.Text.StringBuilder> kesimden dizeleri oluşturmak için sınıfı kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Bir <xref:System.String> nesne değişmez. Bu nedenle, dize herhangi bir değişiklik yeni bir dize nesnesi ve özgün çöp toplama oluşturur. String.Concat'i açıkça çağırıp çağırmadığınız veya + veya +=. Bu yöntemler sık çağrıldığında (örneğin, karakterlerin sıkı bir döngü içinde bir dizeye eklenmesi gibi) program performansı düşebilir.

 StringBuilder sınıfı mutable bir nesnedir ve System.String'in aksine, StringBuilder'da bu sınıfın bir örneğini değiştiren yöntemlerin çoğu aynı örne bir başvuru döndürer. StringBuilder örneğine karakter ekleyebilir veya metin ekleyebilir ve yeni bir örnek ayırmaya ve özgün örneği silmeye gerek kalmadan örnekteki karakterleri kaldırabilir veya değiştirebilirsiniz.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Örnekleme profili verilerinin [İşlev Ayrıntıları Görünümü'ne](../profiling/function-details-view.md) gitmek için **Hata Listesi** penceresindeki iletiyi çift tıklatın. Programın dize birleşmesini en sık kullanan bölümlerini bulun. Sık sık dize concatenation işlemleri de dahil olmak üzere karmaşık dize işlemeleri için StringBuilder sınıfını kullanın.

 Dizeleri ile nasıl çalışacağı hakkında daha fazla bilgi için, Bölüm 5 [String İşlemleri](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) bölümü - Microsoft Desenler ve Uygulamalar kitaplığında Yönetilen Kod [Performansını İyileştirme.](/previous-versions/msp-n-p/ff647790(v=pandp.10))
