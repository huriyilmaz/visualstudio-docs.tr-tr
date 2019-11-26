---
title: 'DA0024: aşırı GC CPU zamanı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0414e8bc4b5789f08751749b52f870c7c5e5167
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300088"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Aşırı GC CPU Süresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0024 |  
| Kategori |. NET Framework kullanımı |  
| Profil oluşturma yöntemi | Tümü |  
| GC 'de% | zamanı çok yüksek. Aşırı miktarda çöp toplama ek yükü vardır. |  
| Kural türü | Uyarı |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 Profil oluşturma sırasında toplanan sistem performansı verileri, çöp toplama işleminde harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında aşırı yüksek olduğunu gösterir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.  
  
 Nesil 0 içindeki nesneler sık ve genellikle çok verimli bir şekilde toplanır. 1\. nesil nesneler daha az ve daha az verimli bir şekilde toplanır. Son olarak, kuşak 2 ' deki uzun süreli nesneler daha az sıklıkta toplanmalıdır. Eksiksiz bir atık toplama çalıştırması olan 2. nesil koleksiyon, ayrıca en pahalı işlemdir.  
  
 Bu kural, çöp toplama sırasında harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında çok yüksek olduğu durumlarda ateşlenir.  
  
> [!NOTE]
> Çöp toplama sırasında harcanan sürenin oranı önemli ve Toplam uygulama işleme süresi ile karşılaştırıldığında çok fazla olmadığında, bu kural yerine [DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md) uyarısı ateşlenir.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Profil oluşturma verilerinin [Işaretler görünümüne](../profiling/marks-view.md) gitmek Için hatalar Listesi penceresinde iletiye çift tıklayın. GC sütununda **.NET CLR belleği\\% süreyi** bulun. Yönetilen bellek çöp toplamanın yükünün diğer aşamalardan daha ağır olduğu, program yürütmesinin belirli aşamaları olup olmadığını belirleme. GC değerindeki% değerinin değerlerini, **# of Gen 0 koleksiyonlarında**, **Gen 1 koleksiyonlardan**oluşan #/ **Gen 2 koleksiyon** değerlerinin sayısı ile bildirilen çöp toplama hızına göre karşılaştırın.  
  
 GC değerindeki% süresi, bir uygulamanın çöp toplama işlemini gerçekleştirirken harcadığı süreyi toplam işleme miktarına göre rapor etmeye çalışır. GC değerindeki% zamanının çok yüksek bir değeri bildirebildiği, ancak aşırı atık toplama nedeniyle olmadığı durumlar olduğunu unutmayın. GC değerindeki% zamanının hesaplanma şekli hakkında daha fazla bilgi için, MSDN 'de **Maonı 'Nin Web günlüğü** ' nde [farklı araçlar – 4 girişi Ile raporlanan performans verileri arasındaki farka](https://go.microsoft.com/fwlink/?LinkId=177863) bakın. Sayfa hataları oluşmakta veya uygulama çöp toplama sırasında makinede daha yüksek öncelikli iş tarafından önayarlanırsa, GC sayacında% süre bu ek gecikmeleri yansıtır.
