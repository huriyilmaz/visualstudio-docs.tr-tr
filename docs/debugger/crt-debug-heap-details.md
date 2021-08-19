---
title: CRT hata ayıklama yığın ayrıntıları | Microsoft Docs
description: Hata ayıklama yığını, bellek ayırma sorunlarını çözmeye yardımcı olmak için güçlü araçlar sağlar. Araçlar ve bunların sızıntı ve taşmaları gibi sorunlarla nasıl yardım ettikleri hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066869"
---
# <a name="crt-debug-heap-details"></a>CRT Hata Ayıklama Öbeği Ayrıntıları
Bu konu, CRT hata ayıklama yığınına ayrıntılı bir bakış sağlar.

## <a name="contents"></a><a name="BKMK_Contents"></a> Dekiler
[Hata ayıklama yığını ile arabellek taşmaları bulma](#BKMK_Find_buffer_overruns_with_debug_heap)

[Hata ayıklama yığınındaki blok türleri](#BKMK_Types_of_blocks_on_the_debug_heap)

[Yığın bütünlüğünü ve bellek sızıntılarını denetle](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Hata ayıklama yığınını yapılandırma](#BKMK_Configure_the_debug_heap)

[C++ hata ayıklama yığınında yeni, silme ve _CLIENT_BLOCKs](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Yığın durumu raporlama Işlevleri](#BKMK_Heap_State_Reporting_Functions)

[Yığın ayırma Isteklerini izleme](#BKMK_Track_Heap_Allocation_Requests)

## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Hata ayıklama yığını ile arabellek taşmaları bulma
Programcıların karşılaştığı en yaygın ve kapsamlı olmayan sorunlardan ikisi, ayrılmış bir arabelleğin ve bellek sızıntılarının sonunun üzerine yazılır (artık gerekli olmadıklarında ayırmaları serbest bırakılamaz). Hata ayıklama yığını, bu türdeki bellek ayırma sorunlarını çözmeye yönelik güçlü araçlar sağlar.

Yığın işlevlerinin hata ayıklama sürümleri, yayın yapılarında kullanılan standart veya temel sürümleri çağırır. Bir bellek bloğu istediğinizde, hata ayıklama yığın Yöneticisi, taban yığınından istemciden biraz daha büyük bir bellek bloğunu ayırır ve bu bloğun bölümüne bir işaretçi döndürür. Örneğin, uygulamanızın çağrıyı içerdiğini varsayalım: `malloc( 10 )` . Bir yayın derlemesinde, [malloc](/cpp/c-runtime-library/reference/malloc) 10 baytlık bir ayırma isteyen temel yığın ayırma yordamını çağırır. Ancak, bir hata ayıklama derlemesinde `malloc` [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)çağırır, bu, daha sonra 10 baytlık bir ayırma ve yaklaşık 36 bayt ek bellek isteyen temel yığın ayırma yordamını çağırırdı. Hata ayıklama yığınındaki tüm ortaya çıkan bellek blokları, ayrıldıklarında, tek bir bağlantılı listeye bağlanır ve bunlara göre sıralanır.

Hata ayıklama yığını yordamları tarafından ayrılan ek bellek, hata ayıklama belleği bloklarını birlikte bağlayan işaretçiler için ve verilerinizin her iki tarafında bulunan küçük arabellekler için, ayrılan bölgenin üzerine yazma bilgilerini yakalamak için kullanılır.

Şu anda, hata ayıklama yığınının kitap tutma bilgilerini depolamak için kullanılan blok üst bilgisi yapısı DBGINT içinde aşağıdaki gibi bildirilmiştir. H üst bilgi dosyası:

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

`NoMansLand`Bloğun Kullanıcı verisi alanının her iki tarafındaki arabellekler şu anda 4 bayttır ve Kullanıcı bellek bloğunun sınırlarının üzerine yazılmadığını doğrulamak için hata ayıklama yığını yordamları tarafından kullanılan bilinen bir bayt değeriyle doldurulur. Hata ayıklama yığını, bilinen bir değere sahip yeni bellek bloklarını da doldurur. Serbest bırakılan blokları, aşağıda açıklandığı gibi yığının bağlantılı listesinde tutmayı tercih ederseniz, bu serbest bırakılan bloklar da bilinen bir değerle doldurulur. Şu anda kullanılan gerçek bayt değerleri şunlardır:

NoMansLand (0xFD) bir uygulama tarafından kullanılan belleğin her iki tarafındaki "NoMansLand" arabellekleri Şu anda 0xFD ile doldurulmuştur.

Serbest bırakılan bloklar (0xDD) `_CRTDBG_DELAY_FREE_MEM_DF` bayrak ayarlandığında, şu anda 0xDD ile doldurulmuş olan, hata ayıklama yığınının bağlantılı listesinde kullanılmamış olan serbest bırakılmış bloklar.

Yeni nesneler (0xCD) yeni nesneler, ayrıldıklarında, 0xCD ile doldurulmuştur.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Hata ayıklama yığınındaki blok türleri
Hata ayıklama yığınındaki her bellek bloğu, beş ayırma türünden birine atanır. Bu türler, sızıntı algılama ve durum raporlama amaçları için izlenir ve farklı şekilde raporlanır. Bir bloğun türünü, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)gibi hata ayıklama yığın ayırma işlevlerinden birine doğrudan çağrı kullanarak ayırarak belirtebilirsiniz. Hata ayıklama yığınındaki beş tür bellek bloğu ( **_CrtMemBlockHeader** yapısının **nblockuse** üyesinde ayarlanır) aşağıdaki gibidir:

**_NORMAL_BLOCK** [Malloc](/cpp/c-runtime-library/reference/malloc) veya [calloc](/cpp/c-runtime-library/reference/calloc) çağrısı normal bir blok oluşturur. Yalnızca normal blokları kullanmayı düşünüyorsanız ve Istemci blokları için ihtiyacınız yoksa, tüm yığın ayırma çağrılarının hata ayıklama yapılarında hata ayıklama eşdeğerlerine eşlenmesine neden olan [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)tanımlamak isteyebilirsiniz. Bu, her bir ayırma çağrısıyla ilgili dosya adı ve satır numarası bilgilerinin karşılık gelen blok üstbilgisinde depolanmasını sağlar.

`_CRT_BLOCK` Birçok çalışma zamanı kitaplığı işlevi tarafından dahili olarak ayrılan bellek blokları, ayrı işlenebilmeleri için CRT blokları olarak işaretlenir. Sonuç olarak, sızıntı algılama ve diğer işlemlerin bunlardan etkilenmemesi gerekir. Bir ayırma hiçbir şekilde hiçbir CRT türü için hiçbir blok ayırmayı, yeniden ayırmayı veya boşaltmayı içermemelidir.

`_CLIENT_BLOCK` Bir uygulama, hata ayıklama yığını işlevlerine yönelik açık çağrılar kullanılarak, bu tür bir bellek bloğu olarak ayırarak, belirli bir ayırma grubunu hata ayıklama amacıyla özel olarak takip edebilir. Örneğin MFC, tüm **CObjects** istemci blokları olarak ayırır; diğer uygulamalar, Istemci bloklarında farklı bellek nesnelerini tutabilir. Istemci bloklarının alt türleri, daha fazla izleme ayrıntı düzeyi için de belirtilebilir. Istemci bloklarının alt türlerini belirtmek için, sayıyı 16 bit ve ile sola kaydırın `OR` `_CLIENT_BLOCK` . Örnek:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

Istemci bloklarına depolanan nesneleri dökme için istemci tarafından sağlanan bir kanca işlevi [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanılarak yüklenebilir ve sonra bir hata ayıklama işlevi tarafından bir istemci bloğu dökütilidiğinde çağırılır. Ayrıca, hata ayıklama yığınındaki her Istemci bloğu için uygulama tarafından sağlanan belirli bir işlevi çağırmak için [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) kullanılabilir.

**_free_block** Normalde, serbest bırakılan bloklar listeden kaldırılır. Serbest bırakılan belleğin, düşük bellek koşullarına benzetmek için veya ' ı benzemekte olup olmadığını denetlemek için, serbest bırakılan blokları bağlantılı listede tutmayı seçebilirsiniz ve bilinen bir bayt değeriyle (Şu anda 0xDD) doldurulmuş olarak işaretlenir.

**_IGNORE_BLOCK** Hata ayıklama yığın işlemlerini bir süre devre dışı bırakmak mümkündür. Bu süre boyunca, bellek blokları listede tutulur, ancak yoksayma blokları olarak işaretlenir.

Belirli bir bloğun türünü ve alt türünü öğrenmek için [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) işlevini ve makroları **_BLOCK_TYPE** ve **_BLOCK_SUBTYPE** kullanın. Makrolar (Crtdbg. h 'de) aşağıdaki gibi tanımlanır:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Yığın bütünlüğünü ve bellek sızıntılarını denetle
Hata ayıklama yığını özelliklerinin çoğuna kodunuzun içinden erişilmelidir. Aşağıdaki bölümde bazı özellikler ve bunların nasıl kullanılacağı açıklanmaktadır.

`_CrtCheckMemory` Örneğin, yığın bütünlüğünü herhangi bir noktada denetlemek için [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)bir çağrı kullanabilirsiniz. Bu işlev, yığındaki her bellek bloğunu inceler, bellek bloğu üstbilgi bilgisinin geçerli olduğunu doğrular ve arabelleklerin değiştirilmediğini onaylar.

`_CrtSetDbgFlag` Hata ayıklama yığınının bir iç bayrak kullanarak ayırmaları nasıl tutacağını denetleyebilir, [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) işlevi kullanılarak okunabilir ve ayarlanabilir. Bu bayrağı değiştirerek, hata ayıklama yığınına program çıktığında bellek sızıntılarını denetlemesini ve algılanan sızıntıları kontrol etmek için talimat verebilirsiniz. Benzer şekilde, düşük bellek durumlarının benzetimini yapmak için, serbest bırakılan bellek bloklarının bağlantılı listeden kaldırılmadığını belirtebilirsiniz. Yığın işaretlendiğinde, bu serbest bırakılan bloklar tamamen incelendiğinden emin olmak için tümüyle denetlenir.

**_CrtDbgFlag** bayrağı aşağıdaki bit alanlarını içerir:

|Bit alanı|Varsayılan<br /><br /> değer|Açıklama|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|Açık|Hata ayıklama ayırmasını etkinleştirir. Bu bit kapalı olduğunda, ayırmalar birlikte kalır ancak blok türü **_IGNORE_BLOCK**.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Kapalı|Düşük bellek koşullarının benzetimini yaparken olduğu gibi, gerçekten serbest bırakılmakta olan belleği önler. Bu bit açık olduğunda, serbest bırakılan bloklar hata ayıklama yığınının bağlantılı listesinde tutulur, ancak **_free_block** olarak işaretlenir ve özel bir bayt değeri ile doldurulur.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Kapalı|**_CrtCheckMemory** her ayırma ve ayırmayı kaldırma sırasında çağrılmasına neden olur. Bu, yürütmeyi yavaşlatır, ancak hataları hızla yakalar.|
|**_CRTDBG_CHECK_CRT_DF**|Kapalı|Tür **_CRT_BLOCK** olarak işaretlenen blokların, sızıntı algılama ve durum farkı işlemlerine dahil edilmesini sağlar. Bu bit devre dışı bırakıldığında, bu işlem sırasında çalışma zamanı kitaplığı tarafından dahili olarak kullanılan bellek yok sayılır.|
|**_CRTDBG_LEAK_CHECK_DF**|Kapalı|**_CrtDumpMemoryLeaks** çağrısı aracılığıyla Program çıkışında sızıntı denetimi gerçekleştirilmesine neden olur. Uygulama, ayrılan tüm belleği serbest Devretmeyen bir hata raporu oluşturulur.|

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Hata ayıklama yığınını yapılandırma
,,,, Ve gibi yığın işlevlerine yapılan tüm çağrılar `malloc` , `free` `calloc` `realloc` `new` `delete` hata ayıklama yığınında çalışan işlevlerin hata ayıklama sürümleriyle çözümlenir. Bir bellek bloğunu serbest bırakırsanız, hata ayıklama yığını ayrılan alanın her iki tarafındaki arabelleklerin bütünlüğünü otomatik olarak denetler ve üzerine yazma oluştuysa bir hata raporu yayınlar.

**Hata ayıklama yığınını kullanmak için**

- Uygulamanızın hata ayıklama derlemesini C çalışma zamanı kitaplığının hata ayıklama sürümüyle ilişkilendirin.

  **Bir veya daha fazla _crtDbgFlag bit alanını değiştirmek ve bayrak için yeni bir durum oluşturmak için**

1. `_CrtSetDbgFlag` `newFlag` Parametresi `_CRTDBG_REPORT_FLAG` (geçerli durumu almak için) olarak ayarlanmış `_crtDbgFlag` ve döndürülen değeri geçici bir değişkende depolayacak şekilde çağırın.

2. Her türlü bitleri `OR` (bit düzeyinde &#124; simgesi), karşılık gelen bit maskeleriyle birlikte geçici değişkeni (bildirim sabitlerine göre uygulama kodunda gösterilir) etkinleştirin.

3. Değişkeni uygun bit maskelerinin `AND` (bitwise ~ simgesi) ile -ing (bit & simgesi) ile diğer `NOT` bitleri kapatın.

4. parametresinin `_CrtSetDbgFlag` yeni durumunu oluşturmak için geçici `newFlag` değişkende depolanan değere ayarlanmış parametresiyle çağrısı. `_crtDbgFlag`

   Örneğin, aşağıdaki kod satırları otomatik sızıntı algılamayı ve tür bloklarını denetlemeyi devre dışı `_CRT_BLOCK` çevirir:

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

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> C++ hata ayıklama \_ yığınında new, delete ve CLIENT \_ BLOCKs
C çalışma zamanı kitaplığının hata ayıklama sürümleri C++ ve işleçlerinin hata `new` ayıklama `delete` sürümlerini içerir. Ayırma türünü kullanırsanız, aşağıdaki örnekte gösterildiği gibi, doğrudan işlecinin hata ayıklama sürümünü çağırmalı veya işleci hata ayıklama modundan alan `_CLIENT_BLOCK` `new` `new` makrolar oluşturabilirsiniz:

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

İşlecinin Hata Ayıklama sürümü tüm blok türleriyle çalışır ve bir Yayın sürümünü derlerken `delete` programda değişiklik gerektirir.

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a> Yığın Durumu Raporlama İşlevleri
 **_CrtMemState**

 Yığının belirli bir zamanda durumunun özet anlık görüntüsünü yakalamak için CRTDBG'de tanımlanan _CrtMemState yapısını kullanın. H:

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

Bu yapı, hata ayıklama yığınının bağlı listesinde ilk (en son ayrılan) bloğuna bir işaretçi kaydeder. Ardından, iki dizide, her bir bellek bloğu türünün (_NORMAL_BLOCK, , _FREE_BLOCK gibi) listede kaç tane olduğunu ve her blok türünde ayrılan bayt sayısını `_CLIENT_BLOCK` kayıt eder. Son olarak, yığında ayrılan en yüksek bayt sayısını o noktaya kadar bir bütün olarak ve şu anda ayrılmış olan bayt sayısını da kaydeder.

**Diğer CRT Raporlama İşlevleri**

Aşağıdaki işlevler yığının durumunu ve içeriğini rapor eder ve bellek sızıntılarını ve diğer sorunları algılamaya yardımcı olmak için bu bilgileri kullanır.

|İşlev|Açıklama|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Uygulama tarafından sağlanan bir _CrtMemState **anlık** görüntüsünü kaydeder.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|İki bellek durumu yapısını karşılar, aralarındaki farkı üçüncü durum yapısına kaydeder ve iki durum farklıysa TRUE döndürür.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Verilen bir veri **_CrtMemState** dökümleri. Yapı, hata ayıklama yığınının durumunun anlık görüntüsünü veya iki anlık görüntü arasındaki farkı içerebilir.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Verilen anlık görüntü yığının alınmasından veya yürütmenin başlangıcından itibaren ayrılan tüm nesnelerle ilgili bilgilerin dökümlerini oluşturur. Bir uygulama bloğunun **döküm _CLIENT_BLOCK** her dökümde, uygulama tarafından sağlanan bir kanca işlevi çağrılır. Bu işlev, _CrtSetDumpClient. |
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Program yürütmenin başlamasından bu yana herhangi bir bellek sızıntısı olup olmadığını belirler ve bu durumda ayrılan tüm nesnelerin dökümlerini verir. Bir **_CrtDumpMemoryLeaks** **bloğunun döküm _CLIENT_BLOCK** her dökümde, uygulama tarafından sağlanan bir kanca işlevi çağrılır **_CrtSetDumpClient**.|

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a> Yığın Ayırma İsteklerini izleme
Bir onay veya raporlama makros unalarının yürütültülürken kaynak dosya adını ve satır numarasını bulmak genellikle bir sorunun nedenini bulmak için çok yararlı olsa da, yığın ayırma işlevleri için de aynı durum doğru değildir. Makrolar bir uygulamanın mantıksal ağacında birçok uygun noktanın üzerine eklenebilirken, ayırma genellikle birçok farklı yerde birçok farklı yerde çağrılmış özel bir yordamda gömülür. Burada soru genellikle hatalı ayırma yapan kod satırı değil, bu kod satırı tarafından yapılan binlerce ayırmadan hangisinin hatalı ve neden olduğudur.

**Benzersiz Ayırma İstek Numaraları ve _crtBreakAlloc**

Kötü giden belirli yığın ayırma çağrısını belirlemenin en basit yolu, hata ayıklama yığınında her bir blokla ilişkili benzersiz ayırma isteği numarası yararlanmaktır. Bir blokla ilgili bilgiler döküm işlevlerinden biri tarafından raporlandığı zaman, bu ayırma isteği numarası küme ayraçları içine alınır (örneğin, " {36} ").

Hatalı ayrılan bir bloğun ayırma isteği numarasını biliyor olduktan sonra, kesme noktası [oluşturmak için _CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) bu slayı geçesiniz. Yürütme bloğu ayrılmadan hemen önce kesmeye neden olur ve hatalı çağrıdan hangi yordamın sorumlu olduğunu belirlemek için geri dönebilirsiniz. Yeniden derlemeyi önlemek için, hata ayıklayıcıda aynı şeyi  gerçekleştirmek için _crtBreakAlloc ayırma isteği numarasına ayarlarsanız bunu gerçekleştirebilirsiniz.

**Ayırma Yordamlarının Hata Ayıklama Sürümlerini Oluşturma**

Biraz daha karmaşık bir yaklaşım, yığın ayırma işlevlerinin _dbg kendi ayırma **yordamlarının** Hata Ayıklama [sürümlerini oluşturmaktır.](../debugger/debug-versions-of-heap-allocation-functions.md) Daha sonra kaynak dosya ve satır numarası bağımsız değişkenlerini temel yığın ayırma yordamları aracılığıyla iletirsiniz ve hatalı ayırmanın nereden kaynaklandığını hemen görebilirsiniz.

Örneğin, uygulamanıza aşağıdakine benzer yaygın olarak kullanılan bir yordam içerdiğini varsayalım:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

Bir üst bilgi dosyasında aşağıdaki gibi kod abilirsiniz:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

Ardından, kayıt oluşturma yordamınız içinde ayırmayı aşağıdaki gibi değiştirebilirsiniz:

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

Artık çağrılan kaynak dosya adı ve satır numarası, hata ayıklama yığınında ayrılan her bir sonuçtaki blokta depolanır ve bu blok `addNewRecord` incelendiğinde raporlanır.

![En Üst İçerikler'e](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [geri dön](#BKMK_Contents)

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
