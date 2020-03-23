---
title: 'DA0007: Kontrol akışı için özel durumlar kullanmaktan kaçının | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26819be7cd001e87a6f94ac97d29c8a5e67f3932
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777705"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının

|||
|-|-|
|Kural Id|DA0007|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Tümü|
|İleti|Çok sayıda özel durum sürekli olarak atılıyor. Program mantığında özel durumların kullanımını azaltmayı düşünün.|
|Mesaj türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Atılan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Özel durum işleyicilerinin hatalarını ve program yürütmesini bozan diğer olayları yakalamak için kullanılması iyi bir uygulama olsa da, normal program yürütme mantığının bir parçası olarak özel durum işleyicisinin kullanımı pahalı olabilir ve kaçınılmalıdır. Çoğu durumda, özel durumlar yalnızca seyrek olarak ortaya çıkan ve beklenmeyen durumlar için kullanılmalıdır. Özel durumlar, değerleri normal program akışının bir parçası olarak döndürmek için kullanılmamalıdır. Çoğu durumda, değerleri doğrulayarak ve soruna neden olan ifadelerin yürütülmesini durdurmak için koşullu mantık kullanarak özel durumlar yükseltmekten kaçınabilirsiniz.

 Daha fazla bilgi için, MSDN'deki **Microsoft Desenler ivedilik** kitaplığının **.NET Uygulama Performansını ve Ölçeklenebilirlik** düzeyini Artırmada **Yönetilen Kod Performansını İyileştirme Bölüm 5'in** [Özel Durum Yönetimi](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Markalar görünümüne gitmek için Hata Listesi penceresindeki iletiyi çift tıklatın. **.NET CLR@ProcessInstanceÖzel Durumları()\\# Excels Thrown / sn ölçümlerini** içeren sütunu bulun. Özel durum işlemenin diğerlerinden daha sık olduğu program yürütmenin belirli aşamaları olup olmadığını belirleyin. Örnekleme profilini kullanarak, atma deyimlerini tanımlamaya çalışın ve sık sık özel durumlar oluşturan blokları deneyin/yakalamayı deneyin. Gerekirse, hangi özel durumların en sık işlendiğini anlamanıza yardımcı olmak için blokları yakalamak için mantık ekleyin. Mümkünse, sık sık yürütülen atma deyimleri değiştirin veya basit akış denetimi mantığı veya doğrulama kodu ile blokları yakalayın.

 Örneğin, uygulamanızın sık sık DivideByZeroException özel durumları işleme olduğunu bulmak için, sıfır değerleri ile paydalar için kontrol etmek için programınıza mantık ekleyerek uygulamanın performansını artırır.
