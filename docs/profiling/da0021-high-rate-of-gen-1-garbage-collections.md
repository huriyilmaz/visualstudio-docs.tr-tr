---
description: Profil oluşturma sırasında toplanan sistem performansı verileri, nesil 0 veri toplamaya kıyasla atık toplamanın 1. neslinde bellek for.NET Framework nesnelerinin önemli bir oranının geri toplanmış olduğunu gösterir.
title: DA0021 - Yüksek oranda 1. Nesil atık toplama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ed53e6999c07f712268be9163f8baa1225e2341
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637113"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Yüksek oranda 1. nesil atık toplama

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0021|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Tümü|
|İleti|1. Nesil çöp toplama işlemlerinin oldukça yüksek bir oranı vardır. Tasarıma göre, program veri yapılarının çoğu uzun bir süre için ayrılır ve kalıcı olursa, bu normalde bir sorun değildir. Ancak, bu davranış istenmişse, uygulamanız nesneleri sabitlemektedir. Emin değilsanız, uygulamanın kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini topabilirsiniz.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 7'niz olduğunda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri, nesil 0 veri toplamaya kıyasla atık toplamanın 1. neslinde bellek for.NET Framework nesnelerinin önemli bir oranının geri toplanmış olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Yaygın Microsoft .NET çalışma zamanı (CLR), uygulamanın artık kullanmama durumuna sahip nesnelerden belleği geri alan bir atık toplayıcı kullanan otomatik bir bellek yönetimi mekanizması sağlar. Atık toplayıcı, çok sayıda ayırmanın kısa süreli olduğu varsayımı üzerine oluşturma odaklıdır. Örneğin yerel değişkenler kısa süreli olmalı. Yeni oluşturulan nesneler nesil 0'da (0. nesil) başlar ve bir çöp toplama çalıştırması çalıştırılana kadar hayatta kalarak 1. nesile ilerler ve uygulama hala bunları kullanıyorsa son olarak 2. nesile geçişler.

 Nesil 0'daki nesneler sıklıkla ve genellikle çok verimli bir şekilde toplanır. Nesil 1'de nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2'de uzun süreli nesneler daha az sıklıkta toplanabilir. Tam çöp toplama çalıştırması olan 2. nesil toplama da en pahalı işlemdir.

 Bu kural, orantılı olarak çok fazla nesil 1 çöp toplaması meydana geldiğinde sızıyor. Çok fazla sayıda kısa süreli nesne nesil 0 koleksiyonuna dayansa da nesil 1 koleksiyonunda toplanabilirse, bellek yönetiminin maliyeti aşırıya iner. Daha fazla bilgi [](/archive/blogs/ricom/mid-life-crisis) için MSDN Web sitesinde, Mariani'nin Performans Tidbit'leri ile ilgili Orta yaş kriz gönderisine bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerinin İşaretler Görünümüne gitmek için Hatalar Listesi [penceresindeki iletiye](../profiling/marks-view.md) çift tıklayın. **\\ 0. Nesil Koleksiyonlar'ın .NET CLR** Belleği ve **\\ 1.** Nesil Koleksiyonlar sütunlarının .NET CLR Belleği # yolunu bulun. Atık toplamanın daha sık olduğu belirli program yürütme aşamaları olup olmadığını belirler. Yönetilen bellek ayırma **desenlerinin aşırı** bellek yönetimi ek yüküne neden olup olmadığını görmek için bu değerleri GC sütunundaki Süre % ile karşılaştırın.

 Uygulamanın yönetilen bellek kullanımı desenini anlamak için, bellek ayırma profiline a.NET ve Nesne Ömrü ölçümlerini isteğinde bulundurarak uygulamanın profilini oluşturun.

 Atık toplama performansını geliştirme hakkında daha fazla bilgi için Microsoft Web sitesinde Atık Toplayıcı temel bilgileri [ve](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) Performans İpuçları makalesine bakın. Otomatik çöp toplamanın ek yükü hakkında bilgi için bkz. [Ele Geçen Büyük Nesne Yığını.](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered)
