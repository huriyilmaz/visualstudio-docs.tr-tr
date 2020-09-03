---
title: DA0007-denetim akışı için özel durumlar kullanmaktan kaçının | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a33d5b8d18f18fb6bf7a2420603d994d845ce8f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520802"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0007|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Tümü|
|İleti|Yüksek sayıda özel durum sürekli olarak oluşturulur. Program mantığındaki özel durumların kullanımını azaltmayı göz önünde bulundurun.|
|Mesaj türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Oluşturulan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı göz önünde bulundurun.

## <a name="rule-description"></a>Kural açıklaması
 Hataları ve program yürütmesini kesintiye uğratan diğer olayları yakalamak için özel durum işleyicilerinin kullanılması iyi bir uygulamadır, ancak özel durum işleyicisinin normal program yürütme mantığının bir parçası olarak kullanılması pahalı olabilir ve kaçınılmalıdır. Çoğu durumda, özel durumlar yalnızca seyrek oluşan ve beklenmediği durumlar için kullanılmalıdır. Özel durumlar, normal program akışının bir parçası olarak değer döndürmek için kullanılmamalıdır. Birçok durumda, değerleri doğrulayarak ve soruna neden olan deyimlerin yürütülmesini durdurmak için koşullu mantığı kullanarak özel durumlar oluşturmaktan kaçınabilirsiniz.

 Daha fazla bilgi için, MSDN 'deki **Microsoft desenleri ve uygulamalar** kitaplığı 'Nın **.NET uygulama performansını ve ölçeklenebilirlik birimini geliştirme** bölümünde **yönetilen kod performansını artırma başlıklı Bölüm 5** ' in [özel durum yönetimi](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Işaretler görünümüne gitmek için Hata Listesi penceresindeki iletiye çift tıklayın. **.NET CLR özel durumlarını () içeren sütunu bul @ProcessInstance \\ oluşturulan/sn** ölçü birimi sayısı. Özel durum işlemenin diğerlerinden daha sık olduğu belirli program yürütme aşamaları olup olmadığını belirleme. Bir örnekleme profili kullanarak, throw deyimlerini tanımlamayı ve sık karşılaşılan özel durumlar oluşturan try/catch bloklarını kullanmayı deneyin. Gerekirse, en sık hangi özel durumların işlendiğini anlamanıza yardımcı olması için catch bloklarına mantık ekleyin. Mümkün olduğunda, sık yürütülen throw deyimlerini veya catch bloklarını basit akış denetim mantığı veya doğrulama kodu ile değiştirin.

 Örneğin, uygulamanızın sık karşılaşılan Dividebysıfırlaması özel durum özel durumlarını işleme olduğunu fark ediyorsanız, sıfır değerli bir değer içeren paydaları denetlemek için programınıza mantık eklemek, uygulamanın performansını geliştirir.
