---
title: CRT kitaplığı ile bellek sızıntılarını bulma | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb2729dcaf0da41c0adac24b0e1909a6d2697eb6
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829940"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT kitaplığı ile bellek sızıntılarını bulma

Bellek sızıntıları, C/C++ Apps 'teki en hafif ve algılayan hata hataları arasındadır. Bellek sızıntıları, daha önce ayrılan belleği doğru şekilde serbest bırakma hatasından kaynaklanır. Küçük bir bellek sızıntısı ilk başta fark olmayabilir, ancak zaman içinde uygulamanın belleği tükendiği zaman düşük performanstan oluşan zayıf performans sorunlarına neden olabilir. Tüm kullanılabilir belleği kullanan bir sızan uygulama, diğer uygulamaların kilitlenmesine neden olabilir ve uygulamanın sorumlu olduğu konusunda karışıklık oluşturur. Hatta zararsız bellek sızıntıları, düzeltilmesi gereken diğer sorunları gösteriyor olabilir.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı ve C çalışma zamanı kitaplığı (CRT), bellek sızıntılarını tespit etmenize ve belirlemenize yardımcı olabilir.

## <a name="enable-memory-leak-detection"></a>Bellek sızıntısı algılamayı etkinleştir

Bellek sızıntılarını algılamaya yönelik birincil araçlar C/C++ Debugger ve c çalışma zamanı KITAPLıĞı (CRT) hata ayıklama yığını işlevleridir.

Tüm hata ayıklama yığını işlevlerini etkinleştirmek için aşağıdaki deyimlerini C++ programınıza aşağıdaki sırayla ekleyin:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` deyimi, CRT yığın işlevlerinin temel sürümünü ilgili hata ayıklama sürümüyle eşler. `#define` deyimden ayrıldıysanız, bellek sızıntısı dökümü [daha az ayrıntılı](#interpret-the-memory-leak-report)olacaktır.

*Crtdbg. h* dahil olmak üzere `malloc` ve `free` işlevleri, bellek ayırmayı ve ayırmayı izleyen hata ayıklama sürümleri, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) ve [_free_dbg](/cpp/c-runtime-library/reference/free-dbg)eşler. Bu eşleme olan yalnızca `_DEBUG` olan hata ayıklama yapılarında, oluşur. Sürüm yapıları sıradan `malloc` ve `free` işlevler kullanır.

Yukarıdaki deyimleri kullanarak hata ayıklama yığın işlevlerini etkinleştirdikten sonra, uygulama çıkarken bir bellek sızıntısı raporu göstermek için bir uygulama çıkış noktasına bir [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) çağrısı koyun.

```cpp
_CrtDumpMemoryLeaks();
```

Uygulamanız birden fazla çıkış içeriyorsa, `_CrtDumpMemoryLeaks` her çıkış noktasında el ile yerleştirmeniz gerekmez. Her çıkış noktasında `_CrtDumpMemoryLeaks` otomatik olarak çağrıya neden olmak için, burada gösterilen bit alanlarıyla uygulamanızın başlangıcına bir `_CrtSetDbgFlag` çağrısı koyun:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Varsayılan olarak, `_CrtDumpMemoryLeaks` **Çıkış** penceresinin **hata ayıklama** bölmesine bellek sızıntısı raporunu çıkarır. Kitaplık kullanıyorsanız, kitaplık çıktıyı başka bir konuma sıfırlayabilir.

Raporu başka bir konuma yönlendirmek veya burada gösterildiği gibi **Çıkış** penceresine geri dönmek için `_CrtSetReportMode` kullanabilirsiniz:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Bellek sızıntısı raporunu yorumlama

Uygulamanız `_CRTDBG_MAP_ALLOC`tanımlamıyorsa, aşağıdaki gibi görünen bir bellek sızıntısı raporu görüntüler [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) :

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Uygulamanız `_CRTDBG_MAP_ALLOC`tanımlıyorsa, bellek sızıntısı raporu şöyle görünür:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

İkinci rapor, sızdırılan belleğin ilk ayrıldığı dosya adını ve satır numarasını gösterir.

`_CRTDBG_MAP_ALLOC`tanımlamadığınız, bellek sızıntısı raporu şunları gösterir:

- Örnekteki `18` bellek ayırma numarası
- Blok türü, örnekteki `normal`.
- Onaltılık bellek konumu, örnekteki `0x00780E80`.
- Bloğun boyutu, örnekteki `64 bytes`.
- Onaltılık biçiminde bloktaki ilk 16 baytlık veri.

Bellek bloğu türleri *normal*, *istemci*veya *CRT*. *Normal bir blok* , programınız tarafından ayrılan sıradan bellektir. *İstemci bloğu* , MFC programları tarafından yıkıcı gerektiren nesneler için kullanılan özel bir bellek bloğu türüdür. MFC `new` işleci normal bir blok veya oluşturulan nesne için uygun bir istemci bloğu oluşturur.

CRT *bloğu* , kendi kullanımı için CRT kitaplığı tarafından ayrılır. CRT kitaplığı bu bloklar için ayırmayı gerçekleştirir, bu nedenle CRT kitaplığı ile ciddi sorunlar olmadıkça, bellek sızıntısı raporunda CRT blokları görünmez.

Hiçbir zaman bellek sızıntısı raporlarında görünmeyen başka iki tür bellek bloğu vardır. *Serbest bir blok* , serbest bırakılmış ve bu nedenle tanım sızdırılmaz bellektir. *Yoksayma bloğu* , bellek sızıntısı raporundan dışlamak üzere açıkça işaretlediğiniz bellektir.

Yukarıdaki teknikler, standart CRT `malloc` işlevi kullanılarak ayrılan bellek sızıntılarını belirler. Programınız C++ `new` işlecini kullanarak bellek ayırırsa, yalnızca `operator new` çağıran dosya adı ve satır numarasını bellek sızıntısı raporunda `_malloc_dbg` görebilirsiniz. Daha kullanışlı bir bellek sızıntısı raporu oluşturmak için, ayırmayı yapan satırı raporlamak üzere aşağıdaki gibi bir makro yazabilirsiniz:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Artık `new` işlecini kodunuzda `DBG_NEW` makrosunu kullanarak değiştirebilirsiniz. Hata ayıklama yapılarında `DBG_NEW`, blok türü, dosya ve satır numarası için ek parametreler alan genel `operator new` aşırı yüklemesini kullanır. `new` aşırı yüklemesi, ek bilgileri kaydetmek için `_malloc_dbg` çağırır. Bellek sızıntısı raporlarında, sızdırılan nesnelerin ayrıldığı dosya adı ve satır numarası gösterilir. Yayın derlemeleri hala varsayılan `new`kullanır. Aşağıda bir teknik örnek verilmiştir:

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Visual Studio hata ayıklayıcıda bu kodu çalıştırdığınızda `_CrtDumpMemoryLeaks` çağrısı, **Çıkış** penceresinde şuna benzer bir rapor oluşturur:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Bu çıktı, sızdırılan ayırmanın *DEBUG_NEW. cpp.*

>[!NOTE]
>`new`veya başka bir dil anahtar sözcüğü adlı bir önişlemci makrosu oluşturmanızı önermiyoruz.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Bir bellek ayırma numarasında kesme noktaları ayarlayın

Bellek ayırma sayısı size bir sızdırılan bellek bloğunun ne zaman ayrıldığını söyler. 16. bellek ayırma numarasına sahip bir blok, örneğin, uygulamanın çalıştırılması sırasında ayrılan belleğin 18of bloğu olur. CRT raporu, çalışma sırasında, CRT kitaplığı ve MFC gibi diğer kitaplıkların ayırmaları dahil tüm bellek bloğu ayırmalarını sayar. Bu nedenle, bellek ayırma blok numarası 18 muhtemelen kodunuz tarafından ayrılan bir 18 bellek bloğu değildir.

Bellek ayırmada bir kesme noktası ayarlamak için ayırma sayısını kullanabilirsiniz.

**İzleme penceresi kullanarak bir bellek ayırma kesme noktası ayarlamak için:**

1. Uygulamanızın başlangıcına yakın bir kesme noktası ayarlayın ve hata ayıklamayı başlatın.

1. Uygulama kesme noktasında durakladığında, **hata ayıkla** > **Windows** > **Izle** ' yi seçerek bir **izleme** penceresi açın (veya **2**. **izleyin**veya **4**. izleyin).

1. **Gözcü** penceresinde **ad** sütununa `_crtBreakAlloc` yazın.

   CRT kitaplığının çok iş parçacıklı DLL sürümünü (/MD seçeneği) kullanıyorsanız, bağlam işlecini ekleyin: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Hata ayıklama simgelerinin yüklendiğinden emin olun. Aksi takdirde `_crtBreakAlloc`, *tanımlanamayan*olarak bildirilir.

1. Tuşuna **girin**.

   Hata ayıklayıcı çağrıyı değerlendirir ve sonucu **değer** sütununa koyar. Bellek ayırmaları üzerinde herhangi bir kesme noktası ayarlanmamışsa bu değer **-1** olacaktır.

1. **Değer** sütununda, değeri hata ayıklayıcının kesilmesini istediğiniz bellek ayırmasının ayırma numarasıyla değiştirin.

Bir bellek ayırma numarasında bir kesme noktası ayarladıktan sonra, hata ayıklamaya devam edin. Aynı koşulların altında çalıştığından emin olun, böylece bellek ayırma numarası değişmez. Programınız belirtilen bellek ayırmaya kesildiğinde, belleğin ayrıldığı koşulları öğrenmek için **çağrı yığını** penceresini ve diğer hata ayıklama pencerelerini kullanın. Daha sonra, nesneye ne olduğunu gözlemlemek ve neden düzgün şekilde serbest bırakılmadığını belirlemek için yürütmeye devam edebilirsiniz.

Nesnede veri kesme noktası ayarlamak da yardımcı olabilir. Daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

Kodda bellek ayırma kesme noktaları da ayarlayabilirsiniz. Şunları yapabilirsiniz:

```cpp
_crtBreakAlloc = 18;
```

 veya:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Bellek durumlarını karşılaştırın
 Bellek sızıntılarının bulunmasına yönelik başka bir teknik de, uygulamanın temel noktalardaki bellek durumunun anlık görüntülerinin alınmasını içerir. Uygulamanızdaki belirli bir noktada bellek durumunun anlık görüntüsünü almak için bir `_CrtMemState` yapısı oluşturun ve `_CrtMemCheckpoint` işlevine geçirin.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint` işlevi yapıyı geçerli bellek durumunun bir anlık görüntüsüyle doldurur.

`_CrtMemState` yapısının içeriğini çıkarmak için yapıyı `_ CrtMemDumpStatistics` işlevine geçirin:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics`, aşağıdaki gibi görünen bellek durumunun dökümünü verir:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Bir kod bölümünde bellek sızıntısı oluşup oluşmadığını belirlemek için, bölümden önce ve sonra bellek durumunun anlık görüntülerini alabilir ve sonra iki durumu karşılaştırmak için `_ CrtMemDifference` komutunu kullanabilirsiniz:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference`, `s1` ve `s2` bellek durumlarını karşılaştırır ve (`s3`) içinde `s1` ve `s2`arasındaki fark olan bir sonuç döndürür.

Bellek sızıntılarını bulmanın bir tekniği, uygulamanızın başlangıcında ve sonunda `_CrtMemCheckpoint` çağrıları yerleştirip sonuçları karşılaştırmak için `_CrtMemDifference` kullanarak başlar. `_CrtMemDifference` bir bellek sızıntısı gösteriyorsa, sızıntı kaynağını yalıtana kadar programınızı bir ikili arama kullanarak bölmek için daha fazla `_CrtMemCheckpoint` çağrısı ekleyebilirsiniz.

## <a name="false-positives"></a>Yanlış pozitif durumlar
 `_CrtDumpMemoryLeaks`, kitaplık, iç ayırmaları CRT blokları veya istemci blokları yerine normal bloklar olarak işaretlerse, bellek sızıntılarına ilişkin hatalı göstergeler verebilir. Bu durumda, `_CrtDumpMemoryLeaks`, kullanıcı tahsisleri ve dahili kitaplık ayırmaları arasındaki farkı anlatamıyor. Kitaplık ayırmalarının genel yıkıcıları, `_CrtDumpMemoryLeaks` öğesini çağırdığınız noktadan sonra çalışırsa, her iç kitaplık ayırması bir bellek sızıntısı olarak bildirilir. Visual Studio .NET ' den önceki standart Şablon Kitaplığı sürümleri, `_CrtDumpMemoryLeaks` bu hatalı pozitif sonuçları rapormasına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [CRT hata ayıklama öbeği ayrıntıları](../debugger/crt-debug-heap-details.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
