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
ms.openlocfilehash: 22307c44e4f82056887fadf6e8fde9e1449a19a5
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247939"
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

Belirli bir bloğun türünü ve alt türünü öğrenmek için [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) işlevini ve makroları **_BLOCK_TYPE** ve **_BLOCK_SUBTYPE**kullanın. Makrolar (Crtdbg. h 'de) aşağıdaki gibi tanımlanır:

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
|**_CRTDBG_LEAK_CHECK_DF**|Kapalı|**_CrtDumpMemoryLeaks**çağrısı aracılığıyla Program çıkışında sızıntı denetimi gerçekleştirilmesine neden olur. Uygulama, ayrılan tüm belleği serbest Devretmeyen bir hata raporu oluşturulur.|

![En üst](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Hata ayıklama yığınını yapılandırma
,,,, Ve gibi yığın işlevlerine yapılan tüm çağrılar `malloc` , `free` `calloc` `realloc` `new` `delete` hata ayıklama yığınında çalışan işlevlerin hata ayıklama sürümleriyle çözümlenir. Bir bellek bloğunu serbest bırakırsanız, hata ayıklama yığını ayrılan alanın her iki tarafındaki arabelleklerin bütünlüğünü otomatik olarak denetler ve üzerine yazma oluştuysa bir hata raporu yayınlar.

**Hata ayıklama yığınını kullanmak için**

- Uygulamanızın hata ayıklama derlemesini C çalışma zamanı kitaplığının hata ayıklama sürümüyle ilişkilendirin.

  **Bir veya daha fazla _crtDbgFlag bit alanını değiştirmek ve bayrak için yeni bir durum oluşturmak için**

1. `_CrtSetDbgFlag` `newFlag` Parametresi `_CRTDBG_REPORT_FLAG` (geçerli durumu almak için) olarak ayarlanmış `_crtDbgFlag` ve döndürülen değeri geçici bir değişkende depolayacak şekilde çağırın.

2. Her türlü bitleri `OR` (bit düzeyinde &#124; simgesi), karşılık gelen bit maskeleriyle birlikte geçici değişkeni (bildirim sabitlerine göre uygulama kodunda gösterilir) etkinleştirin.

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
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Belirli bir anlık görüntü yığının alındığı veya yürütme başlangıcından bu yana ayrılan tüm nesneler hakkındaki bilgileri döker. **_CLIENT_BLOCK** bloğunun her dökümünü yaptığınızda uygulama tarafından sağlanan bir kanca işlevini çağırır, bu, biri **_CrtSetDumpClient**kullanılarak yüklenmişse.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Program yürütme başlangıcından bu yana herhangi bir bellek sızıntılarının oluşup oluşmadığını belirler ve varsa, tüm ayrılan nesneleri döker. Bir **_CLIENT_BLOCK** bloğunun dökümünü **_CrtDumpMemoryLeaks** her seferinde uygulama tarafından sağlanan bir kanca işlevini çağırır, bunlardan biri **_CrtSetDumpClient**kullanılarak yüklenmiştir.|

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
