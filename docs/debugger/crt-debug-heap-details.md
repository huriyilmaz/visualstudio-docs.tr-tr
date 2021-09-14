---
title: CRT Hata Ayıklama Yığın Ayrıntıları | Microsoft Docs
description: Hata ayıklama yığını, bellek ayırma sorunlarını çözmeye yardımcı olmak için güçlü araçlar sağlar. Araçlar ve sızıntılar ve taşma gibi sorunlarda nasıl yardımcı olduklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2714de8b6c93931832fdf5e00e1f22462e2d6e58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630836"
---
# <a name="crt-debug-heap-details"></a>CRT Hata Ayıklama Öbeği Ayrıntıları
Bu konu, CRT hata ayıklama yığınına ayrıntılı bir bakış sağlar.

## <a name="contents"></a><a name="BKMK_Contents"></a> Içeriği
[Hata ayıklama yığını ile arabellek taşmalarını bulma](#BKMK_Find_buffer_overruns_with_debug_heap)

[Hata ayıklama yığınında blok türleri](#BKMK_Types_of_blocks_on_the_debug_heap)

[Yığın bütünlüğünü ve bellek sızıntılarını denetleme](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Hata ayıklama yığınını yapılandırma](#BKMK_Configure_the_debug_heap)

[C++ hata ayıklama yığınında _CLIENT_BLOCKs, silme ve silme](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Yığın Durumu Raporlama İşlevleri](#BKMK_Heap_State_Reporting_Functions)

[Yığın Ayırma İsteklerini izleme](#BKMK_Track_Heap_Allocation_Requests)

## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Hata ayıklama yığını ile arabellek taşmalarını bulma
Programcıların karşılaştığı en yaygın ve takip edilemez sorunlardan ikisi, ayrılan arabellek ve bellek sızıntılarının (artık gerekli kalmadan ayırmaları serbest bırakamama) sonunun üzerine yazmaktır. Hata ayıklama yığını, bu tür bellek ayırma sorunlarını çözmek için güçlü araçlar sağlar.

Yığın işlevlerinin Hata Ayıklama sürümleri, Yayın derlemeleri için kullanılan standart veya temel sürümleri çağrılır. Bir bellek bloğu isteğide bulunurken, hata ayıklama yığın yöneticisi temel yığından istenenden biraz daha büyük bir bellek bloğu ayırır ve bu bloğun bölümünüz için bir işaretçi döndürür. Örneğin, uygulamanıza şu çağrıyı içerdiğini varsayalım: `malloc( 10 )` . Yayın [derlemesinde, malloc](/cpp/c-runtime-library/reference/malloc) 10 bayt ayırma isteğinde bulundurarak temel yığın ayırma yordamını çağırmış olur. Ancak, bir Hata Ayıklama derlemesinde, _malloc_dbg çağrısında bulunur ve bu da 10 bayt ve yaklaşık 36 bayt ek bellek ayırma isteğinde bulunan temel yığın ayırma `malloc` yordamını çağırmış [](/cpp/c-runtime-library/reference/malloc-dbg)olur. Hata ayıklama yığınında ortaya çıkan tüm bellek blokları, ayrılan zamanlara göre sıralandırılan tek bir bağlantılı listede bağlanır.

Hata ayıklama yığın yordamları tarafından ayrılan ek bellek, ayırma bilgilerini, hata ayıklama bellek bloklarını bir araya bağlayacak işaretçiler için ve ayrılmış bölgenin üzerine yazmalarını yakalamak için verilerinizin her iki tarafındaki küçük arabellekler için kullanılır.

Şu anda, hata ayıklama yığınının muhasebe bilgilerini depolamak için kullanılan blok üst bilgisi yapısı DBGINT'de aşağıdaki gibi bildirmiştir. H üst bilgi dosyası:

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

Bloğun kullanıcı veri alanı her iki tarafındaki arabellekler şu anda 4 bayt boyutundadır ve kullanıcının bellek bloğu sınırlarının üzerine yazılmadığını doğrulamak için hata ayıklama yığın yordamları tarafından kullanılan bilinen bir bayt değeriyle `NoMansLand` doldurulur. Hata ayıklama yığını, yeni bellek bloklarını bilinen bir değerle de doldurur. Aşağıda açıklanan şekilde boş blokları yığının bağlantılı listesinde tutmayı seçersiniz, bu serbest bırakılmış bloklar da bilinen bir değerle doldurulur. Şu anda kullanılan gerçek byte değerleri aşağıdaki gibidir:

NoMansLand (0xFD) Bir uygulama tarafından kullanılan belleğin herhangi bir tarafındaki "NoMansLand" arabellekleri şu anda 0xFD.

Serbest bırakılan bloklar (0xDD) Bayrak şu anda boş olduğunda serbest bırakılan bloklar hata ayıklama yığınının bağlantılı listesinde `_CRTDBG_DELAY_FREE_MEM_DF` kullanılmamış 0xDD.

Yeni nesneler (0xCD) Yeni nesneler, 0xCD yeni nesnelerle doldurulur.

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Hata ayıklama yığınında blok türleri
Hata ayıklama yığınında her bellek bloğu beş ayırma türünden biri olarak atanır. Bu türler, sızıntı algılama ve durum raporlama amacıyla farklı bir şekilde iz altına alındı ve raporlandı. Bir bloğun türünü, örneğin _malloc_dbg gibi hata ayıklama yığın ayırma işlevlerinden biri için doğrudan bir çağrı kullanarak [_malloc_dbg.](/cpp/c-runtime-library/reference/malloc-dbg) Hata ayıklama yığınında beş bellek bloğu türü (_CrtMemBlockHeader yapısının **nBlockUse** **üyesinde** ayarlanır) aşağıdaki gibidir:

**_NORMAL_BLOCK** Malloc veya [calloc](/cpp/c-runtime-library/reference/malloc) çağrısı [Normal](/cpp/c-runtime-library/reference/calloc) bir blok oluşturur. Yalnızca Normal bloklar kullanmayı arıyorsanız ve İstemci bloklarına ihtiyacınız yoksa, [hata](/cpp/c-runtime-library/crtdbg-map-alloc)ayıklama derlemelerinde tüm yığın ayırma çağrılarının kendi hata ayıklama eşdeğerleriyle eşlenmiş olmasına neden olan _CRTDBG_MAP_ALLOC 'i tanımlamak istemeniz gerekir. Bu, her ayırma çağrısıyla ilgili dosya adı ve satır numarası bilgilerini ilgili blok üst bilgisinde depolar.

`_CRT_BLOCK` Birçok çalışma zamanı kitaplık işlevi tarafından dahili olarak ayrılan bellek blokları, ayrı olarak işlendiklerine göre CRT blokları olarak işaretlenir. Sonuç olarak, sızıntı algılama ve diğer işlemler bu işlemlerden etkilenmez. Ayırma hiçbir zaman CRT türünde herhangi bir bloğu ayırmalı, yeniden ayırmalı veya serbest bırakmalı.

`_CLIENT_BLOCK` Bir uygulama, hata ayıklama yığını işlevlerine yönelik açık çağrılar kullanarak bu tür bellek bloğu olarak ayırarak, hata ayıklama amacıyla belirtilen ayırma grubunu özel olarak izleyebilir. Örneğin MFC, tüm **CObject'leri İstemci** blokları olarak ayırır; diğer uygulamalar farklı bellek nesnelerini İstemci bloklarında tutabilirsiniz. İstemci bloklarının alt türleri daha fazla izleme ayrıntısı için de belirtilebilir. İstemci bloklarının alt türlerini belirtmek için, s numarayı ile 16 bit sola `OR` `_CLIENT_BLOCK` kaydırın. Örnek:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

İstemci bloklarında depolanan nesnelerin dökümlerini ayıklamak için istemci tarafından sağlanan bir kanca [işlevi, _CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanılarak yüklenir ve ardından bir İstemci bloğu bir hata ayıklama işlevi tarafından her atılmış olduğunda çağrılır. Ayrıca [_CrtDoForAllClientObjects,](/cpp/c-runtime-library/reference/crtdoforallclientobjects) hata ayıklama yığınında her İstemci bloğu için uygulama tarafından sağlanan bir işlevin çağrılmasına da yardımcı olabilir.

**_FREE_BLOCK** Normalde serbest bırakılan bloklar listeden kaldırılır. Boş belleğin yine de yazıldığı veya yetersiz bellek koşullarının benzetimini yaptığı için boş blokları Serbest olarak işaretlenen ve bilinen bir byte değeriyle (şu anda 0xDD) bağlantılı listede tutabilirsiniz.

**_IGNORE_BLOCK** Bir süre için hata ayıklama yığını işlemlerini kapatmak mümkündür. Bu süre boyunca bellek blokları listede tutulur, ancak Blokları yoksay olarak işaretlenir.

Belirli bir bloğun türünü ve alt türünü [](/cpp/c-runtime-library/reference/crtreportblocktype) belirlemek için, _CrtReportBlockType ve _BLOCK_TYPE ve  **_BLOCK_SUBTYPE.** Makrolar aşağıdaki gibi tanımlanır (crtdbg.h içinde):

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Yığın bütünlüğünü ve bellek sızıntılarını denetleme
Hata ayıklama yığınının özelliklerinin birçoğuna kodunuz içinde erişilsin. Aşağıdaki bölümde bazı özellikler ve bunları nasıl kullanabileceğiniz açık almaktadır.

`_CrtCheckMemory` Herhangi bir noktada [yığının bütünlüğünü _CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)için bir çağrısı kullanabilirsiniz. Bu işlev yığında yer alan tüm bellek bloklarını inceler, bellek bloğu üst bilgisi bilgisinin geçerli olduğunu doğrular ve arabelleklerin değiştirilmemesini onaylar.

`_CrtSetDbgFlag`Hata ayıklama yığınının, _crtDbgFlag işlevi kullanılarak okunan ve [](/cpp/c-runtime-library/crtdbgflag)ayarlan _crtDbgFlag iç bayrağını kullanarak ayırmaları [nasıl _CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) kontrol edersiniz. Bu bayrağı değiştirerek, program çıkışta hata ayıklama yığınına bellek sızıntılarını denetlemesini ve algılanan sızıntıları bildirmesini bildirebilirsiniz. Benzer şekilde, yetersiz bellek durumlarının benzetimini yapmak için boş bellek bloklarının bağlantılı listeden kaldırılmasını belirtebilirsiniz. Yığın denetlenirse, serbest bırakılmış bu bloklar tamamen incelenir ve bunların rahatsız ediş etmemesini sağlar.

Aşağıdaki **_crtDbgFlag** bayrağı aşağıdaki bit alanlarını içerir:

|Bit alanı|Varsayılan<br /><br /> değer|Description|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|Açık|Hata ayıklama ayırmayı okur. Bu bit kapalı olduğunda ayırmalar zincirlenmiş olarak kalır ancak blok türü **_IGNORE_BLOCK.**|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Kapalı|Düşük bellek koşullarının benzetisini yapılana kadar belleğin gerçekten serbest bırakılamasını önler. Bu bit açık olduğunda serbest bırakılan bloklar hata ayıklama yığınının bağlı  listesinde tutulur, ancak _FREE_BLOCK olarak işaretlenir ve özel bir bayt değeriyle doldurulur.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Kapalı|Her **ayırma _CrtCheckMemory** ayırma ve ayırmada çağrılma neden olur. Bu, yürütmeyi yavaşlatmakla birlikte hataları hızla yakalar.|
|**_CRTDBG_CHECK_CRT_DF**|Kapalı|Tür olarak işaretlenen **blokların _CRT_BLOCK** algılama ve durum farkı işlemlerine dahil sinen bloklara neden olur. Bu bit kapalı olduğunda, çalışma zamanı kitaplığı tarafından dahili olarak kullanılan bellek bu tür işlemler sırasında yoksayılır.|
|**_CRTDBG_LEAK_CHECK_DF**|Kapalı|program çıkışında, bir çağrısı aracılığıyla gerçekleştirilecek sızıntı denetimine neden **_CrtDumpMemoryLeaks.** Uygulama ayrılmış olan tüm belleği serbest bırakamadı ise bir hata raporu oluşturulur.|

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Hata ayıklama yığınını yapılandırma
, , ve gibi yığın işlevlerine yapılan tüm çağrılar, hata ayıklama yığınında çalışan bu işlevlerin sürümlerinde hata `malloc` `free` `calloc` `realloc` `new` `delete` ayıklamaya çözümler. Bir bellek bloğu serbest bıraksanız, hata ayıklama yığını ayrılan alanınız herhangi bir tarafındaki arabelleklerin bütünlüğünü otomatik olarak denetler ve üzerine yazma gerçekleştiyse bir hata raporu verir.

**Hata ayıklama yığınını kullanmak için**

- C çalışma zamanı kitaplığının hata ayıklama sürümüyle, uygulamanın hata ayıklama derlemesini bağlama.

  **Bir veya daha fazla bit _crtDbgFlag değiştirmek ve bayrağı için yeni bir durum oluşturmak için**

1. parametresi `_CrtSetDbgFlag` olarak ayarlanmış şekilde çağrısı `newFlag` `_CRTDBG_REPORT_FLAG` (geçerli durumu elde etmek için) ve döndürülen değeri geçici bir `_crtDbgFlag` değişkende depolar.

2. Geçici değişkeni karşılık gelen bit maskeleriyle (uygulama kodunda bildirim `OR` sabitleriyle gösterilir) -ing (bitwise &#124; simgesi) ile herhangi bir biti açma.

3. `AND` `NOT` Uygun bit maskelerinden (bit düzeyinde ~ Symbol) oluşan değişkeni (bit düzeyinde & simgesi) devre dışı bırakın.

4. `_CrtSetDbgFlag` `newFlag` İçin yeni durum oluşturmak üzere geçici değişkende depolanan değere ayarlanmış parametre ile çağırın `_crtDbgFlag` .

   Örneğin, aşağıdaki kod satırları otomatik sızıntı algılamayı açıp şu türdeki blokları denetlemeyi devre dışı bırakır `_CRT_BLOCK` :

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>\_C++ hata ayıklama yığınında yeni, silme ve istemci \_ blokları
C çalışma zamanı kitaplığının hata ayıklama sürümleri, C++ ve işleçlerinin hata ayıklama sürümlerini içerir `new` `delete` . `_CLIENT_BLOCK`Ayırma türünü kullanırsanız, işlecin hata ayıklama sürümünü `new` doğrudan çağırmanız ya da `new` Aşağıdaki örnekte gösterildiği gibi, hata ayıklama modundaki işleci değiştirecek makrolar oluşturmanız gerekir:

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

İşlecin hata ayıklama sürümü `delete` tüm blok türleriyle birlikte çalışarak bir yayın sürümü derlerken programınızda hiçbir değişiklik gerektirmez.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a> Yığın durumu raporlama Işlevleri
 **_CrtMemState**

 Belirli bir zamanda yığın durumunun özet anlık görüntüsünü yakalamak için, CRTDBG içinde tanımlanan _CrtMemState yapısını kullanın. Olsun

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

Bu yapı, hata ayıklama yığınının bağlantılı listesindeki ilk (en son ayrılan) bloğuna bir işaretçi kaydeder. Ardından, iki dizide, her bir bellek bloğunun (_NORMAL_BLOCK, `_CLIENT_BLOCK` , _free_block, vb.) kaç sayının listede ve her blok türünde ayrılan baytların sayısını kaydeder. Son olarak, bu noktaya kadar bir bütün olarak yığında ayrılan en yüksek bayt sayısını ve şu anda ayrılan bayt sayısını kaydeder.

**Diğer CRT raporlama Işlevleri**

Aşağıdaki işlevler, yığının durumunu ve içeriğini raporlar ve bu bilgileri kullanarak bellek sızıntılarını ve diğer sorunları algılamaya yardımcı olur.

|İşlev|Açıklama|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Yığının bir anlık görüntüsünü uygulama tarafından sağlanan **_CrtMemState** yapıda kaydeder.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|İki bellek durumu yapılarını karşılaştırır, aralarındaki farkı üçüncü bir durum yapısına kaydeder ve iki durum farklıysa TRUE değerini döndürür.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Verilen bir **_CrtMemState** yapısını döker. Yapı, belirli bir anda hata ayıklama yığınının durumunun bir anlık görüntüsünü veya iki anlık görüntü arasındaki farkı içerebilir.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Belirli bir anlık görüntü yığının alındığı veya yürütme başlangıcından bu yana ayrılan tüm nesneler hakkındaki bilgileri döker. **_CLIENT_BLOCK** bloğunun her dökümünü yaptığınızda uygulama tarafından sağlanan bir kanca işlevini çağırır, bu, biri **_CrtSetDumpClient** kullanılarak yüklenmişse.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Program yürütme başlangıcından bu yana herhangi bir bellek sızıntılarının oluşup oluşmadığını belirler ve varsa, tüm ayrılan nesneleri döker. Bir **_CLIENT_BLOCK** bloğunun dökümünü **_CrtDumpMemoryLeaks** her seferinde uygulama tarafından sağlanan bir kanca işlevini çağırır, bunlardan biri **_CrtSetDumpClient** kullanılarak yüklenmiştir.|

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a> Yığın ayırma Isteklerini izleme
Bir onaylama veya raporlama makrosunun çalıştırıldığı kaynak dosya adı ve satır numarasını işaret eden, genellikle bir sorunun nedenini bulmada çok yararlı olsa da, aynı zamanda yığın ayırma işlevlerinin doğru olması mümkün değildir. Makrolar, bir uygulamanın mantıksal ağacında birçok uygun noktaya eklenebilse de, bir ayırma genellikle birçok farklı yerden çok farklı yerlerden çağrılan özel bir yordama yerleştirilir. Bu soru, genellikle bir kod satırı hatalı bir ayırma yapmadığında, ancak bu kod satırı tarafından yapılan binlerce ayırmalardan birinin hatalı ve neden olduğu anlamına gelir.

**Benzersiz ayırma Isteği numaraları ve _crtBreakAlloc**

Hatalı olan belirli yığın ayırma çağrısını belirlemenin en kolay yolu, hata ayıklama yığınındaki her bir blokla ilişkili benzersiz ayırma isteği numarasından faydalanır. Bir blok hakkındaki bilgiler, döküm işlevlerinden biri tarafından bildirildikleri zaman, bu ayırma isteği numarası küme ayraçları içine alınır (örneğin, " {36} ").

Hatalı ayrılmış bir bloğun ayırma isteği numarasını öğrendikten sonra, bir kesme noktası oluşturmak için bu sayıyı [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) geçirebilirsiniz. Yürütme bloğu ayırmadan hemen önce kesilir ve hatalı çağrıdan hangi yordamın sorumlu olduğunu belirlemek için geri izleyebilirsiniz. Yeniden derlemeden kaçınmak için, **_crtBreakAlloc** hata ayıklayıcıdaki aynı şeyi, ilgilendiğiniz ayırma isteği numarasını ayarlayarak gerçekleştirebilirsiniz.

**Ayırma yordamlarınızın hata ayıklama sürümlerini oluşturma**

Biraz daha karmaşık bir yaklaşım, [yığın ayırma işlevlerinin](../debugger/debug-versions-of-heap-allocation-functions.md) **_dbg** sürümleriyle karşılaştırılabilen kendi ayırma yordamlarınızın hata ayıklama sürümlerini oluşturmaktır. Daha sonra kaynak dosya ve satır numarası bağımsız değişkenlerini temeldeki yığın ayırma yordamlarına geçirebilir ve hatalı bir ayırmanın nereden geldiğini hemen görebilirsiniz.

Örneğin, uygulamanızın şuna benzer şekilde yaygın olarak kullanılan bir yordam içerdiğini varsayalım:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

Üstbilgi dosyasında, aşağıdakiler gibi bir kod ekleyebilirsiniz:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

Ardından, kayıt oluşturma yordamınız içinde ayırmayı aşağıdaki şekilde değiştirebilirsiniz:

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

Artık çağrılan kaynak dosya adı ve satır numarası, `addNewRecord` hata ayıklama yığınında ayrılmış her bir sonuç bloğunda saklanır ve bu blok incelendüğünde raporlanır.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
