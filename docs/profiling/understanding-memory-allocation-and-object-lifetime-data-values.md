---
title: Bellek ayırmayı & nesne yaşam boyu veri değerlerini anlama
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
ms.openlocfilehash: 6eec0c4bc5fc27e07bc04a8445ca14ce538ac376
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780006"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Bellek ayırma ve nesne yaşam boyu veri değerlerini anlama

Profil Oluşturma Araçları'nın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] *.NET bellek ayırma* profil oluşturma yöntemi, bir ayırmada oluşturulan veya çöp koleksiyonunda yok edilen nesnelerin boyutu ve sayısı hakkında bilgi ve olay oluştuğunda işlev çağrı *yığını* hakkında ek bilgiler toplar. *Çağrı yığını,* işlemcide çalıştırılabilen işlevler hakkında bilgi depolayan dinamik bir yapıdır.

Bellek profilleyicisi, profilli bir uygulamada bir .NET Framework nesnesinin her tahsisinde bilgisayar işlemcisini keser. Nesne yaşam boyu verileri de toplandığında, profiloluşturucu her .NET Framework çöp koleksiyonundan sonra işlemciyi keser. Veriler, her profilli işlev ve her nesne türü için toplanır.

## <a name="allocation-data"></a>Tahsis ataveri

Bir .memory olayı oluştuğunda, ayrılan veya yok edilen bellek nesnelerinin toplam sayıları ve boyutları artırılır.

Bir .memory ayırma olayı oluştuğunda, profiloluşturucu çağrı yığınındaki her işlev için örnek sayar artışlar. Veriler toplandığında, arama yığınındaki yalnızca bir işlev şu anda kodu işlev gövdesinde yürütmektedir. Yığındaki diğer işlevler, döndürülmek için çağırdıkları işlevleri bekleyen işlev çağrıları hiyerarşisinde ebeveynlerdir.

- Ayırma olayı için profiloluşturucu, yönergelerini yürüten işlevin *özel* örnek sayısını artar. Özel bir örnek de işlevin toplam *(kapsayıcı)* örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsayıcı örnek sayısı da artar.

- Profil oluşturucu, çağrı yığınındaki diğer tüm işlevlerin dahil örnek sayısını artımlar.

## <a name="lifetime-data"></a>Yaşam boyu veriler

.NET Framework'ün çöp toplayıcısı, uygulamanız için bellek tahsisini ve serbest bırakılmasını yönetir. Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanının çöp toplayıcısı yeni nesneleri nesil 0'da depolar. Koleksiyonlardan kurtulan nesneler 1 ve 2.

Çöp toplayıcı, tüm nesne neslini ayırarak belleği geri alır. Profilli uygulamanın oluşturduğu nesneler için Object Lifetime görünümü, nesnelerin sayısını ve boyutunu ve geri alındıklarında nesli görüntüler.
