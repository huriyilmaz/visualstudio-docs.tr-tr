---
description: Profil oluşturma sırasında toplanan sistem performansı verileri, 1. nesil atık koleksiyonlara kıyasla bellek for.NET Framework nesnelerinin önemli bir oranının 2. nesil atık toplama işleminde geri kazanıldığını gösterir.
title: DA0022-yüksek oranda Gen 2 çöp koleksiyonları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8e5348a73f3a7e99cd86d45d3d59bfe8d6ebed57164fb9468a4c298689f3973f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442573"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Yüksek oranda 2. nesil atık toplama

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0022|
|Kategori|.NET Framework Kullanımıyla|
|Profil oluşturma yöntemi|Tümü|
|İleti|Gerçekleşen çok yüksek miktarda Gen 2 çöp koleksiyonu vardır. Tasarım ile programınızın veri yapılarının çoğu uzun bir süre ayrılır ve kalıcı hale getirilir, bu normalde bir sorun değildir. Ancak, bu davranış istenmeden, uygulamanız nesneleri sabitlenebilir olabilir. Emin değilseniz, uygulamanızın kullandığı bellek ayırma modelini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini toplayabilirsiniz.|
|Kural türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri, 1. nesil atık koleksiyonlara kıyasla bellek for.NET Framework nesnelerinin önemli bir oranının 2. nesil atık toplama işleminde geri kazanıldığını gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.

 Nesil 0 içindeki nesneler sık ve genellikle çok verimli bir şekilde toplanır. 1. nesil nesneler daha az ve daha az verimli bir şekilde toplanır. Son olarak, kuşak 2 ' deki uzun süreli nesneler daha az sıklıkta toplanmalıdır. Eksiksiz bir atık toplama çalıştırması olan 2. nesil koleksiyon, ayrıca en pahalı işlemdir.

 Bu kural, çok sayıda 2. nesil atık toplama işlemi yaparken ateşlenir. iyi davranmış .NET Framework uygulamalar 2. nesil çok sayıda atık koleksiyonu 2. nesil koleksiyonlar olarak 5 ' ten fazla kez olacaktır. (10 x faktörü büyük olasılıkla idealdir.)

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Profil oluşturma verilerinin [Işaretler görünümüne](../profiling/marks-view.md) gitmek Için hatalar Listesi penceresinde iletiye çift tıklayın. **\\ Gen 0 KOLEKSIYONLARıNıN .NET CLR bellek** sayısını ve **\\ Genel 1 koleksiyonlar sütunlarının .NET CLR bellek sayısını** bulun. Çöp toplamanın daha sık gerçekleştiği program yürütmesinin belirli aşamaları olup olmadığını saptayın. Yönetilen bellek ayırmaları deseninin aşırı bellek yönetimi ek yüküne neden olup olmadığını görmek için bu değerleri **GC sütunundaki% Time** ile karşılaştırın.

 2. nesil atık koleksiyonların yüksek oranındaki her zaman bir sorun değildir. Tasarım ile olabilir. Yürütme sırasında uzun süreler için etkin kalması gereken büyük veri yapılarını ayıran bir uygulama, bu kuralı tetikleyebilir. Bu tür bir uygulama bellek baskısı altında olduğunda, sık sık çöp koleksiyonları gerçekleştirmeye zorlanabilir. Daha az maliyetli nesil 0 ve 1. nesil çöp koleksiyonları yalnızca küçük miktarda yönetilen bellek geri kazanılmiyorsa, daha sık 2. nesil atık koleksiyonlar zamanlanır.

 Işaret görünümünde çöp toplama sorunlarını belirlemenize yardımcı olabilecek ek .NET CLR bellek sütunları vardır. **GC sütunundaki% süresi** , bellek yönetimi ek yükünün ne kadar oluştuğunu anlamanıza yardımcı olur. Uygulamanız genellikle çok az sayıda büyük ancak kalıcı nesneler kullanıyorsa, sık kullanılan 2. nesil koleksiyonlar aşırı miktarda CPU süresi tüketmemelidir. Daha fazla fiziksel bellek (RAM) gerektiğinden uygulama bellek baskısı altındaysa, **bellek \ Sayfa/sn** sütun değerlerini değerlendiren ilgili kurallar da harekete çıkabilir.

 Uygulamanın yönetilen bellek kullanımı modelini anlamak için, a.NET bellek ayırma profilini çalıştıran bir kez daha profilini oluşturup nesne ömrü profil oluşturma seçeneğini belirleyin.

 Çöp toplama performansını geliştirme hakkında daha fazla bilgi için bkz. Microsoft Web sitesinde [çöp toplayıcı temelleri ve performans ipuçları](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) . Otomatik atık toplama ek yükü hakkında daha fazla bilgi için bkz. [büyük nesne yığını kapsanmamış](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered).
