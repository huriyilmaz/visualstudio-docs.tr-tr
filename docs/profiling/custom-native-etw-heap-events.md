---
title: Özel Yerli ETW Yığın Olaylar | Microsoft Dokümanlar
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb6f906cbfb715d67f6e10ddcecf094bc25821f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552973"
---
# <a name="custom-native-etw-heap-events"></a>Özel yerel ETW yığın olayları

Visual Studio, yerel bellek profilleyicisi de dahil olmak üzere çeşitli [profil oluşturma ve tanılama araçları](../profiling/profiling-feature-tour.md)içerir.  Bu profiloluşturucu, [ETW olaylarını](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) yığın sağlayıcısından bağlar ve belleğin nasıl tahsis edildiğinin ve kullanıldığının analizini sağlar.  Varsayılan olarak, bu araç yalnızca standart Windows yığınından yapılan ayırmaları çözümleyebilir ve bu yerel yığın dışında herhangi bir ayırma görüntülenmez.

Kendi özel yığınınızı kullanmak ve standart yığından tahsis ataktan kaçınmak isteyebileceğin birçok durum vardır.  Örneğin, [virtualAlloc'u](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) kullanarak uygulamanın veya oyunun başında büyük miktarda bellek ayırabilir ve ardından bu liste deki kendi bloklarınızı yönetebilirsiniz.  Bu senaryoda, bellek profiloluşturucu aracı yalnızca ilk ayırma yı görür, bellek yığını içinde yapılan özel yönetimi değil.  Ancak, Özel Yerel Yığın ETW Sağlayıcısı'nı kullanarak, aracı standart yığın dışında yaptığınız ayırmalar hakkında bildirebilirsiniz.

Örneğin, aşağıdaki gibi bir projede özel bir yığın vardır, `MemoryPool` yalnızca Windows yığınında tek bir ayırma görürsünüz:

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

Özel yığın izleme olmadan [Bellek Kullanımı](../profiling/memory-usage.md) aracından bir anlık görüntü sadece tek 8192 bayt ayırma gösterir ve havuz tarafından yapılan özel ayırmaların hiçbiri:

![Windows yığın ayırma](media/heap-example-windows-heap.png)

Aşağıdaki adımları gerçekleştirerek, özel yığınında bellek usgae izlemek için aynı aracı kullanabilirsiniz.

## <a name="how-to-use"></a>Nasıl kullanılır

Bu kitaplık C ve C++'da kolayca kullanılabilir.

1. Özel yığın ETW sağlayıcısı için üstbilgi ekleyin:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dekoratörü, işaretçiyi `__declspec(allocator)` yeni ayrılan yığın belleğe döndüren özel yığın yöneticinizdeki herhangi bir işleve ekleyin.  Bu dekoratör, aracın döndürülen bellek türünü doğru bir şekilde tanımlamasına olanak tanır.  Örnek:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Bu dekoratör derleyiciye bu işlevin bir ayırıcıya çağrı olduğunu söyleyecektir.  İşleviçin yapılan her arama, çağrı sitesinin adresini, çağrı talimatının boyutunu ve yeni `S_HEAPALLOCSITE` bir simgeye yeni nesnenin typeId'ini çıkaracaktır.  Bir çağrı yığını tahsis edildiğinde, Windows bu bilgileri içeren bir ETW olayı yayacaktır.  Bellek profilleyici aracı, bir `S_HEAPALLOCSITE` sembolle eşleşen bir iade adresi bulmak için çağrı yığınında yürür ve semboldeki typeId bilgileri ayırmanın çalışma zamanı türünü görüntülemek için kullanılır.
   >
   > Kısacası, bu tür olarak `(B*)(A*)MyMalloc(sizeof(B))` araç ta gösterilecek gibi görünen `B`bir `void` `A`çağrı anlamına gelir , değil ya da .

1. C++'da, `VSHeapTracker::CHeapTracker` profil oluşturma aracında gösterilecek yığın için bir ad sağlayan nesneyi oluşturun:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   C kullanıyorsanız, `OpenHeapTracker` bunun yerine işlevi kullanın.  Bu işlev, diğer izleme işlevlerini ararken kullanacağınız bir tanıtıcıyı döndürecektir:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Özel işlevinizi kullanarak belleği ayırırken, ayırmayı izlemek için işaretçiyi belleğe ve boyutuna geçirerek `AllocateEvent` (C++) veya `VSHeapTrackerAllocateEvent` (C) yöntemini arayın:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   or

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Özel ayırıcı işlevinizi daha önce açıklanan `__declspec(allocator)` dekoratörle etiketlemeyi unutmayın.

1. Özel işlevinizi kullanarak belleği ayırırken, ayırmayı izlemek için işaretçiyi `DeallocateEvent` belleğe geçen (C++) veya `VSHeapTracerDeallocateEvent` (C) işlevini çağırın:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   veya:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Özel işlevinizi kullanarak belleği yeniden `ReallocateEvent` ayırırken, (C++) veya `VSHeapReallocateEvent` (C) yöntemini çağırArak yeni belleğe, ayırmanın boyutuna ve eski belleğe işaretçiye geçen bir işaretçiyi seçin:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   veya:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Son olarak, C++'daki özel yığın izleyicisini kapatmak `CHeapTracker` ve temizlemek için, yıkıcıyı el ile veya standart `CloseHeapTracker` kapsam kuralları yla veya C'deki işlevle kullanın:

   ```cpp
   delete pHeapTracker;
   ```

   veya:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Bellek kullanımını izleme
Bu çağrılar yerinde yken, özel yığın kullanımınız artık Visual Studio'daki standart **Bellek Kullanımı** aracı kullanılarak izlenebilir.  Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için lütfen [Bellek Kullanımı](../profiling/memory-usage.md) belgelerine bakın. Anlık görüntülerle yığın profil oluşturmayı etkinleştirdiğinizden emin olun, aksi takdirde özel yığın kullanımınızın görüntülendiğini görmezsiniz.

![Yığın Profil oluşturmayı etkinleştirme](media/heap-enable-heap.png)

Özel yığın izlemenizi görüntülemek için, Görünümü *NT Yığın'dan* daha önce adlandırılmış kendi yığınınıza değiştirmek için **Anlık Görüntü** penceresinin sağ üst köşesinde bulunan **Yığın** açılır penceresini kullanın.

![Yığın Seçimi](media/heap-example-custom-heap.png)

Yukarıdaki kod örneğini `MemoryPool` kullanarak, `VSHeapTracker::CHeapTracker` bir nesne `allocate` oluşturarak ve `AllocateEvent` kendi yöntemimiz şimdi yöntemi çağırarak, şimdi bu özel ayırmanın sonucunu görebilirsiniz, `Foo`toplam da 24 bayt, tüm tür .

Varsayılan *NT Yığın* yığını, nesnemizin `CHeapTracker` eklenmesiyle öncekiyle aynı görünür.

![İzleyici ile NT Yığın](media/heap-example-windows-heap.png)

Standart Windows yığınında olduğu gibi, anlık görüntüleri karşılaştırmak ve ana [Bellek Kullanımı](../profiling/memory-usage.md) belgelerinde açıklanan özel yığınınızdaki sızıntıları ve bozulmaları aramak için de bu aracı kullanabilirsiniz.

> [!TIP]
> Visual Studio ayrıca Hata **Ayıklama** > **Performans Profilleyici** menüsüseçeneğinden veya **Alt**+**F2** klavye kombinasyonundan etkinleştirilen Performans **Profiloluşturma** araç setinde bir Bellek **Kullanımı** aracı içerir.  Bu özellik yığın izleme içermez ve burada açıklandığı gibi özel yığın görüntülemez.  Hata **Ayıklama** > **Windows** > **Show Tanılama Araçları** menüsü veya **Ctrl**+**Alt**+**F2** klavye kombinasyonuyla etkinleştirilebilen **yalnızca Tanılama Araçları** penceresi bu işlevselliği içerir.

## <a name="see-also"></a>Ayrıca bkz.
[Profil oluşturma araçlarına](../profiling/profiling-feature-tour.md)
ilk bakış[Bellek Kullanımı](../profiling/memory-usage.md)
