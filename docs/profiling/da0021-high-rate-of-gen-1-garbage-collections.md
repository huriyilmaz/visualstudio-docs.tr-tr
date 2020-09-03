---
title: DA0021-yüksek oranda Gen 1 çöp koleksiyonları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b22341f1e4944b91f86a16af19494a85a2abd013
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544696"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Yüksek oranda 1. nesil atık toplama

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0021|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Tümü|
|İleti|Gerçekleşen çok yüksek bir gen 1 çöp koleksiyonları vardır. Tasarım ile programınızın veri yapılarının çoğu uzun bir süre ayrılır ve kalıcı hale getirilir, bu normalde bir sorun değildir. Ancak, bu davranış istenmeden, uygulamanız nesneleri sabitlenebilir olabilir. Emin değilseniz, uygulamanızın kullandığı bellek ayırma modelini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini toplayabilirsiniz.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri bellek for.NET Framework nesnelerinin önemli bir oranının, 1. nesil veri toplamaya kıyasla çöp toplamanın 1. kuşak ile geri kazanıldığını gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.

 Nesil 0 içindeki nesneler sık ve genellikle çok verimli bir şekilde toplanır. 1. nesil nesneler daha az ve daha az verimli bir şekilde toplanır. Son olarak, kuşak 2 ' deki uzun süreli nesneler daha az sıklıkta toplanmalıdır. Eksiksiz bir atık toplama çalıştırması olan 2. nesil koleksiyon, ayrıca en pahalı işlemdir.

 Bu kural, çok fazla 1. nesil atık toplama işlemi meydana geldiğinde ateşlenir. Çok sayıda çok kısa süreli nesne nesil 0 toplama işlemi devam ediyor ancak daha sonra 1. nesil bir koleksiyonda toplanıyorsa, bellek yönetiminin maliyeti aşırı olabilir. Daha fazla bilgi için, MSDN Web sitesindeki Riko [maridın](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) performans katmanını ' na bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Profil oluşturma verilerinin [Işaretler görünümüne](../profiling/marks-view.md) gitmek Için hatalar Listesi penceresinde iletiye çift tıklayın. ** \\ Gen 0 KOLEKSIYONLARıNıN .NET CLR bellek** sayısını ve ** \\ Genel 1 koleksiyonlar sütunlarının .NET CLR bellek sayısını** bulun. Çöp toplamanın daha sık gerçekleştiği program yürütmesinin belirli aşamaları olup olmadığını saptayın. Yönetilen bellek ayırmaları deseninin aşırı bellek yönetimi ek yüküne neden olup olmadığını görmek için bu değerleri **GC sütunundaki% Time** ile karşılaştırın.

 Uygulamanın yönetilen bellek kullanımı modelini anlamak için, a.NET bellek ayırma profilini ve istek nesnesi yaşam süresi ölçümlerini çalıştıran bir kez daha profilini yeniden çalıştırın.

 Çöp toplama performansını geliştirme hakkında daha fazla bilgi için bkz. Microsoft Web sitesinde [çöp toplayıcı temelleri ve performans ipuçları](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) . Otomatik atık toplama ek yükü hakkında daha fazla bilgi için bkz. [büyük nesne yığını kapsanmamış](https://msdn.microsoft.com/magazine/cc534993.aspx).
