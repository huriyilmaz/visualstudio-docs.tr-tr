---
title: Bellek ayırma & nesne ömrü verileri değerleri
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b3f7f6785b1a1693e0b041e64a0d507281926d3
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189829"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Bellek ayırmayı ve nesne yaşam süresi veri değerlerini anlama

Profil Oluşturma Araçları *.net bellek ayırma* profili oluşturma yöntemi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir ayırma içinde oluşturulan veya atık toplamada yok edilen nesnelerin boyutu ve sayısı hakkında bilgi ve olay oluştuğunda işlev *çağrı yığını* hakkında ek bilgiler toplar. *Çağrı yığını* , işlemcide yürütülen işlevlerle ilgili bilgileri depolayan dinamik bir yapıdır.

Bellek profili Oluşturucu, profili oluşturulmuş bir uygulamadaki .NET Framework nesnesinin her ayırmada bilgisayar işlemcisini keser. Nesne ömür verileri de toplandığında, Profil Oluşturucu .NET Framework her bir çöp toplama işleminden sonra işlemciyi keser. Veriler, her bir profili oluşturulan işlev ve her nesne türü için toplanır.

## <a name="allocation-data"></a>Ayırma verileri

Bir. Memory olayı gerçekleştiğinde, ayrılan veya yok edilen bellek nesnelerinin toplam sayısı ve boyutları artırılır.

Bir. bellek ayırma olayı gerçekleştiğinde, profil oluşturucu çağrı yığınında her bir işlevin örnek sayılarını arttırır. Veriler toplandığında, çağrı yığınında yalnızca bir işlev şu anda kendi işlev gövdesinde yürütülen kodu yürütüyor. Yığındaki diğer işlevler, döndürmek için çağırdıkları işlevleri bekleyen işlev çağrılarının hiyerarşisinde üstlerdir.

- Ayırma olayı için, profil oluşturucu Şu anda yönergelerini yürüten işlevin *dışlamalı* örnek sayısını artırır. Dışlamalı bir örnek aynı zamanda işlevin toplam (*kapsamlı*) örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsamlı örnek sayısı da artırılır.

- Profiler, Çağrı yığınındaki diğer tüm işlevlerin dahil edilen örnek sayısını artırır.

## <a name="lifetime-data"></a>Ömür verileri

.NET Framework atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir. Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanı atık toplayıcısı yeni nesneleri nesil 0 ' da depolar. Tutulan koleksiyonlar, 1. ve 2. nesil içinde yükseltilerek saklanır.

Tüm nesnelerin neslini ayırmayı kaldırarak çöp toplayıcı geri kazanır belleği. Profili oluşturulan uygulamanın oluşturduğu nesneler için, nesne ömrü görünümü, nesnelerin sayısını ve boyutunu, geri kazanıladıklarında oluşturmayı görüntüler.
