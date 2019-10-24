---
title: CRT hata ayıklama yığın ayrıntıları | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d09319e412d693fc9df95d9ae9b9773f0869afc3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745620"
---
# <a name="crt-debug-heap-details"></a>CRT Hata Ayıklama Öbeği Ayrıntıları
Bu konu, CRT hata ayıklama yığınına ayrıntılı bir bakış sağlar.

## <a name="BKMK_Contents"></a>Dekiler
[Hata ayıklama yığını ile arabellek taşmaları bulma](#BKMK_Find_buffer_overruns_with_debug_heap)

[Hata ayıklama yığınındaki blok türleri](#BKMK_Types_of_blocks_on_the_debug_heap)

[Yığın bütünlüğünü ve bellek sızıntılarını denetle](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Hata ayıklama yığınını yapılandırma](#BKMK_Configure_the_debug_heap)

[C++ hata ayıklama yığınındaki yeni, silme ve _CLIENT_BLOCKs](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Yığın durumu raporlama Işlevleri](#BKMK_Heap_State_Reporting_Functions)

[Yığın ayırma Isteklerini izleme](#BKMK_Track_Heap_Allocation_Requests)

## <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>Hata ayıklama yığını ile arabellek taşmaları bulma
Programcıların karşılaştığı en yaygın ve kapsamlı olmayan sorunlardan ikisi, ayrılmış bir arabelleğin ve bellek sızıntılarının sonunun üzerine yazılır (artık gerekli olmadıklarında ayırmaları serbest bırakılamaz). Hata ayıklama yığını, bu türdeki bellek ayırma sorunlarını çözmeye yönelik güçlü araçlar sağlar.

Yığın işlevlerinin hata ayıklama sürümleri, yayın yapılarında kullanılan standart veya temel sürümleri çağırır. Bir bellek bloğu istediğinizde, hata ayıklama yığın Yöneticisi, taban yığınından istemciden biraz daha büyük bir bellek bloğunu ayırır ve bu bloğun bölümüne bir işaretçi döndürür. Örneğin, uygulamanızın çağrıyı içerdiğini varsayalım: `malloc( 10 )`. Bir yayın derlemesinde, [malloc](/cpp/c-runtime-library/reference/malloc) 10 baytlık bir ayırma isteyen temel yığın ayırma yordamını çağırır. Ancak, bir hata ayıklama derlemesinde, `malloc` [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)öğesini çağırıp, daha sonra 10 baytlık bir ayırma ve yaklaşık 36 bayt ek belleği sağlayan temel yığın ayırma yordamını çağırırdı. Hata ayıklama yığınındaki tüm ortaya çıkan bellek blokları, ayrıldıklarında, tek bir bağlantılı listeye bağlanır ve bunlara göre sıralanır.

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

Bloğun Kullanıcı verisi alanının her iki tarafındaki `NoMansLand` arabellekleri Şu anda 4 bayttır ve kullanıcının bellek bloğunun sınırlarının üzerine yazılmadığını doğrulamak için hata ayıklama yığını yordamları tarafından kullanılan bilinen bir bayt değeriyle doldurulur. Hata ayıklama yığını, bilinen bir değere sahip yeni bellek bloklarını da doldurur. Serbest bırakılan blokları, aşağıda açıklandığı gibi yığının bağlantılı listesinde tutmayı tercih ederseniz, bu serbest bırakılan bloklar da bilinen bir değerle doldurulur. Şu anda kullanılan gerçek bayt değerleri şunlardır:

NoMansLand (0xFD) bir uygulama tarafından kullanılan belleğin her iki tarafındaki "NoMansLand" arabellekleri Şu anda 0xFD ile doldurulmuştur.

Serbest bırakılan bloklar (0xDD) `_CRTDBG_DELAY_FREE_MEM_DF` bayrağı ayarlandığında, şu anda 0xDD ile doldurulmuş olarak, hata ayıklama yığınının bağlantılı listesinde kullanılmamış olan serbest bırakılmış bloklar.

Yeni nesneler (0xCD) yeni nesneler, ayrıldıklarında, 0xCD ile doldurulmuştur.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a>Hata ayıklama yığınındaki blok türleri
Hata ayıklama yığınındaki her bellek bloğu, beş ayırma türünden birine atanır. Bu türler, sızıntı algılama ve durum raporlama amaçları için izlenir ve farklı şekilde raporlanır. [_Malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)gibi hata ayıklama yığın ayırma işlevlerinden birine doğrudan çağrı kullanarak bir bloğun türünü belirtebilirsiniz. Hata ayıklama yığınındaki beş tür bellek bloğu ( **_CrtMemBlockHeader** yapısının **nblockuse** üyesinde ayarlanır) aşağıdaki gibidir:

**_Normal_block** [Malloc](/cpp/c-runtime-library/reference/malloc) veya [calloc](/cpp/c-runtime-library/reference/calloc) çağrısı normal bir blok oluşturur. Yalnızca normal blokları kullanmayı düşünüyorsanız ve Istemci blokları gerekmiyorsa, tüm yığın ayırma çağrılarının hata ayıklama yapılarında hata ayıklama eşdeğerlerine eşlenmesine neden olan [_Crtdbg_map_allocation](/cpp/c-runtime-library/crtdbg-map-alloc)öğesini tanımlamak isteyebilirsiniz. Bu, her bir ayırma çağrısıyla ilgili dosya adı ve satır numarası bilgilerinin karşılık gelen blok üstbilgisinde depolanmasını sağlar.

birçok çalışma zamanı kitaplığı işlevi tarafından dahili olarak ayrılan bellek blokları `_CRT_BLOCK`, ayrı olarak işlenebilmeleri Için CRT bloklar olarak işaretlenir. Sonuç olarak, sızıntı algılama ve diğer işlemlerin bunlardan etkilenmemesi gerekir. Bir ayırma hiçbir şekilde hiçbir CRT türü için hiçbir blok ayırmayı, yeniden ayırmayı veya boşaltmayı içermemelidir.

`_CLIENT_BLOCK` bir uygulama, hata ayıklama yığını işlevlerine açık çağrılar kullanarak, bu tür bir bellek bloğu olarak ayırarak, belirli bir ayırma grubunu hata ayıklama amacıyla özel olarak izlemeyi tutabilir. Örneğin MFC, tüm **CObjects** istemci blokları olarak ayırır; diğer uygulamalar, Istemci bloklarında farklı bellek nesnelerini tutabilir. Istemci bloklarının alt türleri, daha fazla izleme ayrıntı düzeyi için de belirtilebilir. Istemci bloklarının alt türlerini belirtmek için, sayıyı 16 bit sola kaydırın ve `_CLIENT_BLOCK` `OR`. Örneğin:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

Istemci bloklarına depolanan nesneleri dökme için istemci tarafından sağlanan bir kanca işlevi, [_Crtsetdumpclient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanılarak yüklenebilir ve sonra bir hata ayıklama işlevi tarafından bir istemci bloğu dökütilidiğinde çağrılır. Ayrıca, [_Crtdoforallclientobjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) , hata ayıklama yığınındaki her istemci bloğu için uygulama tarafından sağlanan belirli bir işlevi çağırmak için kullanılabilir.

**_Free_block** Normalde, serbest bırakılan bloklar listeden kaldırılır. Serbest bırakılan belleğin, düşük bellek koşullarına benzetmek için veya ' ı benzemekte olup olmadığını denetlemek için, serbest bırakılan blokları bağlantılı listede tutmayı seçebilirsiniz ve bilinen bir bayt değeriyle (Şu anda 0xDD) doldurulmuş olarak işaretlenir.

**_IGNORE_BLOCK** Hata ayıklama yığın işlemlerini bir süre devre dışı bırakmak mümkündür. Bu süre boyunca, bellek blokları listede tutulur, ancak yoksayma blokları olarak işaretlenir.

Belirli bir bloğun türünü ve alt türünü belirlemekte, [_Crtreportblocktype](/cpp/c-runtime-library/reference/crtreportblocktype) ve Macros **_Block_type** ve **_block_subtype**işlevini kullanın. Makrolar (Crtdbg. h 'de) aşağıdaki gibi tanımlanır:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>Yığın bütünlüğünü ve bellek sızıntılarını denetle
Hata ayıklama yığını özelliklerinin çoğuna kodunuzun içinden erişilmelidir. Aşağıdaki bölümde bazı özellikler ve bunların nasıl kullanılacağı açıklanmaktadır.

`_CrtCheckMemory`, örneğin, yığın bütünlüğünü herhangi bir noktada denetlemek için, bir [_Crtcheckmemory](/cpp/c-runtime-library/reference/crtcheckmemory)çağrısı kullanabilirsiniz. Bu işlev, yığındaki her bellek bloğunu inceler, bellek bloğu üstbilgi bilgisinin geçerli olduğunu doğrular ve arabelleklerin değiştirilmediğini onaylar.

`_CrtSetDbgFlag` hata ayıklama yığınının, [_Crtsetdbgflag](/cpp/c-runtime-library/reference/crtsetdbgflag) işlevi kullanılarak okunabilecek ve ayarlanabilmesi için bir iç bayrak, [_Crtdbgflag](/cpp/c-runtime-library/crtdbgflag)kullanarak ayırmaları nasıl izlecağını kontrol edebilirsiniz. Bu bayrağı değiştirerek, hata ayıklama yığınına program çıktığında bellek sızıntılarını denetlemesini ve algılanan sızıntıları kontrol etmek için talimat verebilirsiniz. Benzer şekilde, düşük bellek durumlarının benzetimini yapmak için, serbest bırakılan bellek bloklarının bağlantılı listeden kaldırılmadığını belirtebilirsiniz. Yığın işaretlendiğinde, bu serbest bırakılan bloklar tamamen incelendiğinden emin olmak için tümüyle denetlenir.

**_Crtdbgflag** bayrağı aşağıdaki bit alanlarını içerir:

|Bit alanı|Varsayılan<br /><br /> value|Açıklama|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|Açık|Hata ayıklama ayırmasını etkinleştirir. Bu bit kapalı olduğunda, ayırmalar birbirine zincirleme kalır ancak blok türü **_IGNORE_BLOCK**' dir.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Kapalı|Düşük bellek koşullarının benzetimini yaparken olduğu gibi, gerçekten serbest bırakılmakta olan belleği önler. Bu bit açık olduğunda, serbest bırakılan bloklar hata ayıklama yığınının bağlantılı listesinde tutulur, ancak **_Free_block** olarak işaretlenir ve özel bir bayt değeriyle doldurulur.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Kapalı|**_Crtcheckmemory** 'ın her ayırma ve ayırmayı kaldırma sırasında çağrılmasına neden olur. Bu, yürütmeyi yavaşlatır, ancak hataları hızla yakalar.|
|**_CRTDBG_CHECK_CRT_DF**|Kapalı|Tür **_CRT_BLOCK** olarak işaretlenen blokların, sızıntı algılama ve durum farkı işlemlerine dahil edilmesini sağlar. Bu bit devre dışı bırakıldığında, bu işlem sırasında çalışma zamanı kitaplığı tarafından dahili olarak kullanılan bellek yok sayılır.|
|**_CRTDBG_TAAK_CHECK_DF**|Kapalı|Bir **_Crtdumpmemorysızıntı**çağrısı yoluyla program çıkışında sızıntı denetimi gerçekleştirilmesine neden olur. Uygulama, ayrılan tüm belleği serbest Devretmeyen bir hata raporu oluşturulur.|

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Configure_the_debug_heap"></a>Hata ayıklama yığınını yapılandırma
@No__t_0, `free`, `calloc`, `realloc`, `new` ve `delete` gibi yığın işlevlerine yapılan tüm çağrılar, hata ayıklama yığınında çalışan işlevlerin hata ayıklama sürümleri için çözümlenmesini sağlar. Bir bellek bloğunu serbest bırakırsanız, hata ayıklama yığını ayrılan alanın her iki tarafındaki arabelleklerin bütünlüğünü otomatik olarak denetler ve üzerine yazma oluştuysa bir hata raporu yayınlar.

**Hata ayıklama yığınını kullanmak için**

- Uygulamanızın hata ayıklama derlemesini C çalışma zamanı kitaplığının hata ayıklama sürümüyle ilişkilendirin.

  **Bir veya daha fazla _crtDbgFlag bit alanını değiştirmek ve bayrak için yeni bir durum oluşturmak için**

1. @No__t_1 parametresi `_CRTDBG_REPORT_FLAG` olarak ayarlanmış `_CrtSetDbgFlag` çağırın (geçerli `_crtDbgFlag` durumunu almak için) ve döndürülen değeri geçici bir değişkende depolayın.

2. Herhangi bir bitleri `OR` (bit düzeyinde &#124; simge) ile geçici değişkeni, karşılık gelen bitmaskeleriyle (uygulama kodunda bildirim sabitlerine göre gösterilir) açın.

3. Diğer bitleri `AND` (bit düzeyinde & Symbol) ile uygun bitmaskelerin `NOT` (bit düzeyinde ~ Symbol) olarak kapatın.

4. @No__t_2 için yeni durum oluşturmak üzere geçici değişkende depolanan değere ayarlanan `newFlag` parametresi ile `_CrtSetDbgFlag` çağırın.

   Örneğin, aşağıdaki kod satırları otomatik sızıntı algılamayı açıp `_CRT_BLOCK` tür blokları denetlemeyi devre dışı bırakır:

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

## <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>C++ hata ayıklama yığınındaki yeni, silme ve _CLIENT_BLOCKs
C çalışma zamanı kitaplığının hata ayıklama sürümleri, C++ `new` ve `delete` işleçlerinin hata ayıklama sürümlerini içerir. @No__t_0 ayırma türünü kullanıyorsanız, aşağıdaki örnekte gösterildiği gibi, `new` işlecinin hata ayıklama sürümünü doğrudan çağırmanız veya hata ayıklama modundaki `new` işlecini değiştirecek makrolar oluşturmanız gerekir:

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

@No__t_0 işlecinin hata ayıklama sürümü tüm blok türleriyle birlikte çalışarak bir yayın sürümü derlerken programınızda hiçbir değişiklik gerektirmez.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Heap_State_Reporting_Functions"></a>Yığın durumu raporlama Işlevleri
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

Bu yapı, hata ayıklama yığınının bağlantılı listesindeki ilk (en son ayrılan) bloğuna bir işaretçi kaydeder. Daha sonra, iki dizide her bir bellek bloğunun (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK, vb.) kaç tane bir tür ve her blok türünde ayrılan bayt sayısını kaydeder. Son olarak, bu noktaya kadar bir bütün olarak yığında ayrılan en yüksek bayt sayısını ve şu anda ayrılan bayt sayısını kaydeder.

**Diğer CRT raporlama Işlevleri**

Aşağıdaki işlevler, yığının durumunu ve içeriğini raporlar ve bu bilgileri kullanarak bellek sızıntılarını ve diğer sorunları algılamaya yardımcı olur.

|İşlev|Açıklama|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Yığının bir anlık görüntüsünü uygulama tarafından sağlanan **_Crtmemstate** yapısına kaydeder.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|İki bellek durumu yapılarını karşılaştırır, aralarındaki farkı üçüncü bir durum yapısına kaydeder ve iki durum farklıysa TRUE değerini döndürür.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Verilen bir **_Crtmemstate** yapısının dökümünü yapar. Yapı, belirli bir anda hata ayıklama yığınının durumunun bir anlık görüntüsünü veya iki anlık görüntü arasındaki farkı içerebilir.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Belirli bir anlık görüntü yığının alındığı veya yürütme başlangıcından bu yana ayrılan tüm nesneler hakkındaki bilgileri döker. Bir **_Client_block** bloğunun her dökümünü yaparken, bir uygulama tarafından sağlanan bir kanca işlevini çağırır. Bu, bir **_Crtsetdumpclient**kullanılarak yüklenmişse.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Program yürütme başlangıcından bu yana herhangi bir bellek sızıntılarının oluşup oluşmadığını belirler ve varsa, tüm ayrılan nesneleri döker. **_Crtdumpmemorysızıntıları** **_client_block** bloğunun dökümünü yapar; bu, **_Crtsetdumpclient**kullanılarak yüklenmişse uygulama tarafından sağlanan kanca işlevini çağırır.|

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Track_Heap_Allocation_Requests"></a>Yığın ayırma Isteklerini izleme
Bir onaylama veya raporlama makrosunun çalıştırıldığı kaynak dosya adı ve satır numarasını işaret eden, genellikle bir sorunun nedenini bulmada çok yararlı olsa da, aynı zamanda yığın ayırma işlevlerinin doğru olması mümkün değildir. Makrolar, bir uygulamanın mantıksal ağacında birçok uygun noktaya eklenebilse de, bir ayırma genellikle birçok farklı yerden çok farklı yerlerden çağrılan özel bir yordama yerleştirilir. Bu soru, genellikle bir kod satırı hatalı bir ayırma yapmadığında, ancak bu kod satırı tarafından yapılan binlerce ayırmalardan birinin hatalı ve neden olduğu anlamına gelir.

**Benzersiz ayırma Isteği numaraları ve _Crtbreakkalloc**

Hatalı olan belirli yığın ayırma çağrısını belirlemenin en kolay yolu, hata ayıklama yığınındaki her bir blokla ilişkili benzersiz ayırma isteği numarasından faydalanır. Bir blok hakkındaki bilgiler, döküm işlevlerinden biri tarafından bildirildikleri zaman, bu ayırma isteği numarası küme ayraçları içine alınır (örneğin, "{36}").

Hatalı ayrılmış bir bloğun ayırma isteği numarasını öğrendikten sonra, bir kesme noktası oluşturmak için bu sayıyı [_Crtsetbreakkalloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) 'a geçirebilirsiniz. Yürütme bloğu ayırmadan hemen önce kesilir ve hatalı çağrıdan hangi yordamın sorumlu olduğunu belirlemek için geri izleyebilirsiniz. Yeniden derlemeden kaçınmak için, **_Crtbreakkalloc** 'u ilgilendiğiniz ayırma isteği numarasına ayarlayarak hata ayıklayıcıda aynı şeyi yapabilirsiniz.

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

Artık `addNewRecord` çağrıldığı kaynak dosya adı ve satır numarası, hata ayıklama yığınında ayrılan her sonuç bloğunda saklanır ve bu blok incelendüğünde rapor edilir.

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
