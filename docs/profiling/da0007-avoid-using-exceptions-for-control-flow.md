---
title: DA0007 - Denetim akışı özel durumlarını | Microsoft Docs
description: Profil oluşturma veri .NET Framework yüksek oranda özel durum işleyicileri çağrıldı.
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b6dcf3fe5246a3a0281868f4b7ddf753fcd9511afc48028b4a2a69129892c13
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396753"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0007|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Tümü|
|İleti|Sürekli olarak çok sayıda özel durum sızıyor. Program mantığında özel durum kullanımını azaltmayı göz önünde bulundurabilirsiniz.|
|Mesaj türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 25 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma veri .NET Framework yüksek oranda özel durum işleyicileri çağrıldı. Diğer denetim akışı mantığını kullanarak, atılan özel durumların sayısını azaltmayı göz önünde bulundurarak.

## <a name="rule-description"></a>Kural açıklaması
 Özel durum işleyicilerinin program yürütmeyi kesintiye neden olan hataları ve diğer olayları yakalamak için kullanımı iyi bir uygulamadır, ancak normal program yürütme mantığının bir parçası olarak özel durum işleyicisi kullanımı pahalı olabilir ve kaçınılması gerekir. Çoğu durumda, özel durumlar yalnızca seyrek oluşan ve beklenmiyor olan durumlar için kullanılmalıdır. Özel durumlar, normal program akışının bir parçası olarak değer dönmek için kullanılmamalı. Çoğu durumda, değerleri doğrular ve soruna neden olan deyimlerin yürütülmesini durdurmak için koşullu mantık kullanarak özel durumların önüne geçebilirsiniz.

 Daha fazla bilgi [](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) için MSDN'de **Microsoft Patterns and Practices** kitaplığının .NET Uygulama Performansını ve **Ölçeklenebilirlik** hacmini geliştirme bölümündeki **Bölüm 5 -** Yönetilen Kod Performansını Geliştirme bölümünün Özel Durum Yönetimi bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 İşaretler görünümüne gitmek için Hata Listesi penceresinde iletiye çift tıklayın. **.NET CLR Exceptions( @ProcessInstance ) # \\ of Excel Thrown / sec ölçümlerini içeren** sütunu bulun. Özel durum işlemenin diğerlerine göre daha sık olduğu belirli program yürütme aşamaları olup olmadığını belirler. Örnekleme profili kullanarak, sık sık özel durumlar oluşturan throw deyimlerini ve try/catch bloklarını belirlemeyi deneyin. Gerekirse, hangi özel durumların en sık işlen olduğunu anlamanıza yardımcı olmak için blokları yakalamak için mantık ekleyin. Mümkün olduğunca, sık yürütülen throw deyimlerini veya yakalama bloklarını basit akış denetim mantığı veya doğrulama koduyla değiştirin.

 Örneğin, uygulamanın sık sık DivideByZeroException özel durumlarını işleyeni olduğunu bulursanız, programınıza sıfır değere sahip paydaları denetleme mantığı eklemek uygulamanın performansını artırır.
