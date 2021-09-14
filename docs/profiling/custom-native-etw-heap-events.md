---
title: Özel Yerel ETW Yığın Olayları | Microsoft Docs
description: Ayırma ek yükünü azaltmak için özel yığın kullanmayı öğrenin, ancak yine de ayırma analizi için bellek profilleyiciye ayırma bilgileri sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 497348f4df25a3c26ce20617f00ac3f79e806e27
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637198"
---
# <a name="custom-native-etw-heap-events"></a>Özel yerel ETW yığın olayları

Visual Studio, yerel bellek [profilleyicisi dahil olmak üzere](../profiling/profiling-feature-tour.md)çeşitli profil oluşturma ve tanılama araçları içerir.  Bu profil oluşturma, [yığın sağlayıcısından ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) olaylarını kancalar ve belleğin nasıl ayrılmış ve kullanıldıklarına yönelik analiz sağlar.  Varsayılan olarak, bu araç yalnızca standart Windows yığından yapılan ayırmaları analiz eder ve bu yerel yığının dışındaki ayırmalar görüntülenmez.

Kendi özel yığınınızı kullanmak ve standart yığından ayırma ek yükünden kaçınmak istediğiniz birçok durum vardır.  Örneğin, [virtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) kullanarak uygulamanın veya oyunun başında büyük miktarda bellek ayırabilirsiniz ve ardından bu listede kendi bloklarınızı yönetebilirsiniz.  Bu senaryoda, bellek profil oluşturma aracı yalnızca ilk ayırmayı görebilir ve özel yönetiminiz bellek öbbek içinde yapılmaz.  Ancak, Özel Yerel Yığın ETW Sağlayıcısı'nı kullanarak, standart yığının dışında yapılan tüm ayırmaları aracına haber veebilirsiniz.

Örneğin, aşağıdakine benzer bir projede özel bir yığın olduğu için, tek bir ayırmayı Windows `MemoryPool` görebilirsiniz:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Özel yığın [izlemesi](../profiling/memory-usage.md) olmadan Bellek Kullanımı aracından bir anlık görüntü yalnızca tek 8192 byte ayırmasını gösterir ve havuz tarafından yapılan özel ayırmaların hiçbirini göstermez:

![Windows yığın ayırma](media/heap-example-windows-heap.png)

Aşağıdaki adımları gerçekleştirerek, özel yığınımızda bellek kullanımını izlemek için aynı aracı kullanabiliriz.

## <a name="how-to-use"></a>Nasıl kullanılır?

Bu kitaplık C ve C++ içinde kolayca kullanılabilir.

1. Özel yığın ETW sağlayıcısı için üst bilgi içerir:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dekoratörü `__declspec(allocator)` özel yığın yöneticinizde yeni ayrılan yığın belleğine bir işaretçi döndüren herhangi bir işleve ekleyin.  Bu dekoratör aracın döndürülen belleğin türünü doğru şekilde tanımlamasını sağlar.  Örnek:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Bu dekoratör derleyiciye bu işlevin bir yalıtıcı çağrısı olduğunu söyler.  İşleve yapılan her çağrı, çağrı sitenin adresini, çağrı yönergesi boyutunu ve yeni nesnenin typeId'lerini yeni bir sembole `S_HEAPALLOCSITE` verir.  Bir çağrı yığını ayrılırsa, Windows bu bilgilerle bir ETW olayı yayacağız.  Bellek profil oluşturma aracı, bir sembolle eşleşen bir dönüş adresi arayan çağrı yığınında yol gösterilir ve ayırmanın çalışma zamanı türünü görüntülemek için `S_HEAPALLOCSITE` sembolde typeId bilgileri kullanılır.
   >
   > Kısacası, bu, araçta veya türünde değil gibi `(B*)(A*)MyMalloc(sizeof(B))` görünen bir çağrının göster `B` olduğu `void` anlamına `A` gelir.

1. C++ için, `VSHeapTracker::CHeapTracker` yığın için profil oluşturma aracında gösterecek bir ad sağlayarak nesnesini oluşturun:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   C kullanıyorsanız bunun yerine `OpenHeapTracker` işlevini kullanın.  Bu işlev, diğer izleme işlevlerini çağıran bir tanıtıcıyı geri verir:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Özel işlevinizi kullanarak bellek ayırmada ayırmayı izlemek için `AllocateEvent` (C++) veya (C) yöntemini çağırarak işaretçiyi belleğe ve `VSHeapTrackerAllocateEvent` boyutuna geçirme:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   veya

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Özelocator işlevinizi daha önce açıklanan dekoratörle `__declspec(allocator)` etiketlemeyi unutmayın.

1. Özel işlevinizi kullanarak belleğin yerini alıtırken, ayırmayı izlemek için `DeallocateEvent` (C++) veya (C) işlevini çağırarak işaretçiyi `VSHeapTracerDeallocateEvent` belleğe geçirme:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   veya:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Özel işlevinizi kullanarak belleği yeniden konumlarken `ReallocateEvent` ( C++) veya (C) yöntemini çağırarak yeni belleğe bir işaretçi, ayırmanın boyutu ve eski belleğe bir işaretçi `VSHeapReallocateEvent` geçirme:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   veya:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Son olarak, C++ içinde özel yığın izleyicisini kapatmak ve temizlemek için, yıkıcıyı el ile veya standart kodlama kuralları aracılığıyla veya C'de işlevini `CHeapTracker` `CloseHeapTracker` kullanın:

   ```cpp
   delete pHeapTracker;
   ```

   veya:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Bellek kullanımını izleme
Bu çağrılar olduğu için, özel yığın kullanımınız artık Visual Studio'da **standart** Bellek Kullanımı aracı kullanılarak iz Visual Studio.  Bu aracın kullanımı hakkında daha fazla bilgi için lütfen Bellek Kullanımı [belgelerine](../profiling/memory-usage.md) bakın. Anlık görüntülerle yığın profili oluşturmayı etkinleştirdikten emin olun, aksi takdirde özel yığın kullanımınızı görüntülenmez.

![Yığın Profili Oluşturmayı Etkinleştirme](media/heap-enable-heap.png)

Özel yığın izlemenizi görüntülemek  için Anlık Görüntü penceresinin sağ üst  köşesinde bulunan Yığın açılan penceresini kullanarak *NT Yığını* görünümünü daha önce belirtildiği gibi kendi yığınınıza göre değiştirebilirsiniz.

![Yığın Seçimi](media/heap-example-custom-heap.png)

Yukarıdaki kod örneğini kullanarak, bir nesnesi oluşturulurken ve kendi yöntemimiz artık yöntemini çağırarak, artık bu özel ayırmanın sonucunda toplam `MemoryPool` 24 bayt olmak üzere tüm türünde üç örnek `VSHeapTracker::CHeapTracker` `allocate` `AllocateEvent` `Foo` görebilirsiniz.

Varsayılan *NT Yığın* yığını, nesnemizin ekleriyle birlikte öncekiyle aynı `CHeapTracker` şekilde görünüyor.

![İzleyici ile NT Yığını](media/heap-example-windows-heap.png)

Standart Windows yığınında olduğu gibi, bu aracı kullanarak anlık görüntüleri karşılaştırabilirsiniz ve ana Bellek Kullanımı belgelerinde açıklanan özel yığında sızıntılar ve [bozulmalar bulabilirsiniz.](../profiling/memory-usage.md)

> [!TIP]
> Visual Studio, **Performans** Profili Oluşturma araç  kümesinde Hata Ayıklama menü seçeneğinden veya Alt F2 klavye birleşiminden  >  **etkinleştiren bir Performans Profili Oluşturucu Bellek Kullanımı** aracı da  +  içerir.  Bu özellik yığın izlemesi içermez ve özel yığınınızı burada açıklandığı gibi görüntülemez.  Bu **Tanılama Araçları** Hata Ayıklama Windows Tanılama Araçları göster menüsü veya  >    >   **Ctrl** + **Alt** + **F2** klavye birleşimiyle etkinleştirildikten sonra etkinleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
[Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md) 
 [Bellek Kullanımı](../profiling/memory-usage.md)
