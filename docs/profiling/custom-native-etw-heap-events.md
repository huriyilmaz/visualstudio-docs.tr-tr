---
title: Özel yerel ETW yığın olayları | Microsoft Docs
description: Ayırma yükünü azaltmak için özel bir yığın kullanmayı öğrenin, ancak yine de ayırma analizi için bellek profil oluşturucuya ayırma bilgileri sağlayın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084590"
---
# <a name="custom-native-etw-heap-events"></a>Özel yerel ETW yığın olayları

Visual Studio, yerel bellek oluşturucu dahil olmak üzere çeşitli [profil oluşturma ve tanılama araçları](../profiling/profiling-feature-tour.md)içerir.  Bu profil oluşturucu, yığın sağlayıcısından [ETW olaylarını](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) takar ve belleğin nasıl ayrılacağını ve kullanılmakta olduğunu analiz sağlar.  varsayılan olarak, bu araç yalnızca standart Windows yığınından yapılan ayırmaları analiz edebilir ve bu yerel yığın dışındaki tüm ayırmalar görüntülenmez.

Kendi özel öbekinizi kullanmak isteyebileceğiniz ve standart öbekten ayırma yüküyle karşılaşmamak isteyebileceğiniz birçok durum vardır.  Örneğin, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 'yi uygulama veya oyunun başlangıcında büyük miktarda bellek ayırmak için kullanabilir ve ardından bu liste içinde kendi bloklarınızı yönetebilirsiniz.  Bu senaryoda, bellek Oluşturucu aracı yalnızca ilk ayırmayı görebilir ve özel yönetiğinizin bellek öbeği içinde yapılmadığından emin olur.  Ancak, özel yerel yığın ETW sağlayıcısını kullanarak, aracın standart yığın dışında yaptığınız tüm ayırmalar hakkında bilgi almasına izin verebilirsiniz.

örneğin, aşağıdaki gibi bir projede `MemoryPool` özel bir yığın olduğu gibi, Windows yığınında yalnızca tek bir ayırma görürsünüz:

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

[Bellek kullanımı](../profiling/memory-usage.md) aracından özel yığın izleme olmadan bir anlık görüntü yalnızca tek 8192 baytlık ayırmayı ve havuz tarafından gerçekleştirilen özel ayırmaların hiçbirini göstermez:

![yığın ayırmayı Windows](media/heap-example-windows-heap.png)

Aşağıdaki adımları gerçekleştirerek, bu aracı, özel öbekimizde bellek kullanımını izlemek için de kullanabilirsiniz.

## <a name="how-to-use"></a>Nasıl kullanılır?

Bu kitaplık, C ve C++ ' da kolayca kullanılabilir.

1. Özel yığın ETW sağlayıcısı için üst bilgiyi ekleyin:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. `__declspec(allocator)`Yeni ayrılan yığın belleğine bir işaretçi döndüren özel yığın yöneticinizin herhangi bir işlevine dekoratör ekleyin.  Bu dekoratör, aracın döndürülen bellek türünü doğru şekilde tanımlamasına olanak sağlar.  Örnek:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Bu dekoratör, derleyiciye bu işlevin bir ayırıcı çağrısı olduğunu bildirir.  İşlevine yapılan her çağrı, CallSite adresini, çağrı yönergesinin boyutunu ve yeni nesnenin TypeId değerini yeni bir sembol olarak çıktı `S_HEAPALLOCSITE` .  bir çağrı yığını ayrıldığında Windows, bu bilgilerle bir ETW olayı oluşturacak.  Bellek profili Oluşturucu Aracı, bir sembol ile eşleşen dönüş adresini arayan çağrı yığını 'e kılavuzluk eder `S_HEAPALLOCSITE` ve simgenin içindeki TypeId bilgisi, ayırmanın çalışma zamanı türünü göstermek için kullanılır.
   >
   > Kısacası bu, gibi görünen bir çağrının `(B*)(A*)MyMalloc(sizeof(B))` `B` , ya da değil, araçta görüneceğini gösterir `void` `A` .

1. C++ için, `VSHeapTracker::CHeapTracker` yığın için, profil oluşturma aracında görünecek bir ad sağlayarak nesnesini oluşturun:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   C kullanıyorsanız, `OpenHeapTracker` bunun yerine işlevini kullanın.  Bu işlev, diğer izleme işlevlerini çağırırken kullanacağınız bir tanıtıcı döndürür:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Özel işlevinizi kullanarak bellek ayırırken, `AllocateEvent` ayırmayı izlemek için, (C++) veya `VSHeapTrackerAllocateEvent` (C) yöntemini çağırın, bu durumda, belleğin ve boyutunun boyutuna geçer:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   veya

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Özel ayırıcı işlevinizi, `__declspec(allocator)` daha önce açıklanan dekoratörü ile etiketleyerek unutmayın.

1. Özel işlevinizi kullanarak bellek ayırmayı kaldırdığınızda, `DeallocateEvent` ayırmayı izlemek için, (C++) veya `VSHeapTracerDeallocateEvent` (C) işlevini, belleğe işaretçiyi geçirerek çağırın:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   veya:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Özel işlevinizi kullanarak belleği yeniden konumlandırdığınızda, `ReallocateEvent` (C++) veya `VSHeapReallocateEvent` (C) yöntemini çağırın, yeni belleğe bir işaretçi, ayırmanın boyutu ve eski belleğe yönelik bir işaretçi ile geçer:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   veya:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Son olarak, C++ ' da özel yığın izleyicisini kapatmak ve temizlemek için, `CHeapTracker` yıkıcıyı el ile veya standart kapsam kuralları aracılığıyla veya `CloseHeapTracker` C içindeki işlevi kullanarak kullanın:

   ```cpp
   delete pHeapTracker;
   ```

   veya:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Bellek kullanımını izleme
Bu çağrılar yerine, özel yığın kullanımınız artık Visual Studio içindeki standart **bellek kullanımı** Aracı kullanılarak izlenebilir.  Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için lütfen [bellek kullanımı](../profiling/memory-usage.md) belgelerine bakın. Anlık görüntülerle yığın profili oluşturmayı etkinleştirmiş olduğunuzdan emin olun, aksi takdirde özel yığın kullanımınız görüntülendiğini görmezsiniz.

![Yığın profili oluşturmayı etkinleştir](media/heap-enable-heap.png)

Özel yığın izlemeyi görüntülemek için, **anlık görüntü** penceresinin sağ üst köşesinde bulunan **yığın** açılan listesini kullanarak, görünümü *NT yığınından* daha önce adlandırılan şekilde kendi yığına değiştirin.

![Yığın seçimi](media/heap-example-custom-heap.png)

Yukarıdaki kod örneğini kullanarak `MemoryPool` bir `VSHeapTracker::CHeapTracker` nesne oluşturma ve kendi `allocate` yöntemizin artık `AllocateEvent` yöntemi çağıran, bu özel ayırmanın sonucunu, her bir 24 bayt ön alma, tüm tür olan üç örnek gösteriliyor `Foo` .

Varsayılan *NT yığın* yığını, nesnemizin eklenmesiyle birlikte daha önce de aynı şekilde görünür `CHeapTracker` .

![Izleyici ile NT yığını](media/heap-example-windows-heap.png)

standart Windows yığınında olduğu gibi, anlık görüntüleri karşılaştırmak ve özel yığında, ana [bellek kullanımı](../profiling/memory-usage.md) belgelerinde açıklanan sızıntı ve bozulmaları aramak için bu aracı da kullanabilirsiniz.

> [!TIP]
> Visual Studio ayrıca, **hata ayıklama**    >  **performansı profil oluşturucu** menü seçeneğinden veya **Alt** + **F2** klavye bileşiminin etkin olan performans profili oluşturma araç takımı 'nda bir bellek kullanımı aracı da içerir.  Bu özellik yığın izlemeyi içermez ve burada açıklandığı gibi özel öbekinizi göstermez.  yalnızca **Tanılama Araçları** pencere **hata ayıkla**  >  **Windows**  >  **göster Tanılama Araçları** menüsüyle veya **Ctrl** + **Alt** + **F2** klavye birleşimi ile etkinleştirilebilir, bu işlevi içerir.

## <a name="see-also"></a>Ayrıca bkz.
[Profil oluşturma araçlarına](../profiling/profiling-feature-tour.md) 
 ilk bakış [Bellek kullanımı](../profiling/memory-usage.md)
