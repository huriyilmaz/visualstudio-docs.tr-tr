---
title: CRT kitaplığı ile bellek sızıntılarını bulma | Microsoft Docs
description: C/C++ hata ayıklayıcı ve C çalışma zamanı kitaplığı 'nın (CRT) bellek sızıntılarını bulma konusunda nasıl yardımcı olabileceğini öğrenin. Teknikler, bellek sızıntısı raporlarını ve bellek anlık görüntülerini karşılaştırmayı içerir.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f248d29640f6d8e3cb629d083f6589ec1e173f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030899"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT kitaplığı ile bellek sızıntılarını bulma

Bellek sızıntıları, C/C++ uygulamalarında en hafif ve algılayan hata hataları arasındadır. Bellek sızıntıları, daha önce ayrılan belleği doğru şekilde serbest bırakma hatasından kaynaklanır. Küçük bir bellek sızıntısı ilk başta fark olmayabilir, ancak zaman içinde uygulamanın belleği tükendiği zaman düşük performanstan oluşan zayıf performans sorunlarına neden olabilir. Tüm kullanılabilir belleği kullanan bir sızan uygulama, diğer uygulamaların kilitlenmesine neden olabilir ve uygulamanın sorumlu olduğu konusunda karışıklık oluşturur. Hatta zararsız bellek sızıntıları, düzeltilmesi gereken diğer sorunları gösteriyor olabilir.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Hata ayıklayıcı ve C çalışma zamanı kitaplığı (CRT), bellek sızıntılarını tespit etmenize ve belirlemenize yardımcı olabilir.

## <a name="enable-memory-leak-detection"></a>Bellek sızıntısı algılamayı etkinleştir

Bellek sızıntılarını algılamaya yönelik birincil araçlar C/C++ hata ayıklayıcısıdır ve C çalışma zamanı kitaplığı (CRT) hata ayıklama yığını işlevleridir.

Tüm hata ayıklama yığın işlevlerini etkinleştirmek için, aşağıdaki sırayla C++ programınıza aşağıdaki deyimleri ekleyin:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define`İfade, CRT yığın işlevlerinin temel bir sürümünü karşılık gelen hata ayıklama sürümüne eşler. `#define`Deyimden ayrıldıysanız, bellek sızıntısı dökümü [daha az ayrıntılı](#interpret-the-memory-leak-report)olacaktır.

*Crtdbg. h* dahil olmak üzere, `malloc` ve `free` işlevlerini hata ayıklama sürümleri, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) ve [_free_dbg](/cpp/c-runtime-library/reference/free-dbg)eşler ve bu da bellek ayırmayı ve ayırmayı kaldırma işlemlerini izler. Bu eşleme yalnızca, içeren hata ayıklama yapılarında oluşur `_DEBUG` . Yayın derlemeleri normal `malloc` ve işlevleri kullanır `free` .

Yukarıdaki deyimleri kullanarak hata ayıklama yığın işlevlerini etkinleştirdikten sonra, uygulama çıkarken bir bellek sızıntısı raporu göstermek için bir uygulama çıkış noktasına bir [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) çağrısı koyun.

```cpp
_CrtDumpMemoryLeaks();
```

Uygulamanızda birkaç çıkış varsa, her çıkış noktasında el ile yerleştirmeniz gerekmez `_CrtDumpMemoryLeaks` . Her çıkış noktasında otomatik çağrının yapılmasına neden olmak için `_CrtDumpMemoryLeaks` , `_CrtSetDbgFlag` burada gösterilen bit alanlarıyla uygulamanızın başlangıcına bir çağrısı koyun:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Varsayılan olarak, `_CrtDumpMemoryLeaks` **Çıkış** penceresinin **hata ayıklama** bölmesine bellek sızıntısı raporunu verir. Bir kitaplık kullanıyorsanız, kitaplık çıktıyı başka bir konuma sıfırlayabilir.

`_CrtSetReportMode`Raporu başka bir konuma yeniden yönlendirmek veya burada gösterildiği gibi **Çıkış** penceresine geri dönmek için ' i kullanabilirsiniz:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Bellek sızıntısı raporunu yorumlama

Uygulamanız tanımlanmazsa `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) aşağıdakine benzer bir bellek sızıntısı raporu görüntüler:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Uygulamanız tanımlıyorsa `_CRTDBG_MAP_ALLOC` , bellek sızıntısı raporu şöyle görünür:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

İkinci rapor, sızdırılan belleğin ilk ayrıldığı dosya adını ve satır numarasını gösterir.

Sizin tanımladığınız olsun `_CRTDBG_MAP_ALLOC` , bellek sızıntısı raporu şunları görüntüler:

- Örnekteki bellek ayırma numarası `18`
- Bu, örnekteki blok türüdür `normal` .
- Örnekteki onaltılık bellek konumu `0x00780E80` .
- Örneğin, bloktaki blok boyutu `64 bytes` .
- Blok içindeki ilk 16 baytlık veriler, onaltılık biçimde.

Bellek bloğu türleri *normal*, *istemci* veya *CRT*. *Normal bir blok* , programınız tarafından ayrılan sıradan bellektir. *İstemci bloğu* , MFC programları tarafından yıkıcı gerektiren nesneler için kullanılan özel bir bellek bloğu türüdür. MFC `new` işleci, oluşturulmakta olan nesneye uygun şekilde normal bir blok veya bir istemci bloğu oluşturur.

CRT *bloğu* , kendi kullanımı için CRT kitaplığı tarafından ayrılır. CRT kitaplığı bu bloklar için ayırmayı gerçekleştirir, bu nedenle CRT kitaplığı ile ciddi sorunlar olmadıkça, bellek sızıntısı raporunda CRT blokları görünmez.

Bellek sızıntısı raporlarında hiçbir şekilde görünmeyen iki tür bellek bloğu vardır. *Serbest bir blok* , serbest bırakılmış ve bu nedenle tanım sızdırılmaz bellektir. *Yoksayma bloğu* , bellek sızıntısı raporundan dışlamak üzere açıkça işaretlediğiniz bellektir.

Yukarıdaki teknikler, standart CRT işlevi kullanılarak ayrılan bellek için bellek sızıntılarını belirler `malloc` . Programınız C++ işlecini kullanarak bellek ayırırsa, `new` yalnızca `operator new` bellek sızıntısı raporundaki çağrıların bulunduğu dosya adını ve satır numarasını görebilirsiniz `_malloc_dbg` . Daha kullanışlı bir bellek sızıntısı raporu oluşturmak için, ayırmayı yapan satırı raporlamak üzere aşağıdaki gibi bir makro yazabilirsiniz:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Artık `new` kodunuzda makroyu kullanarak işleci değiştirebilirsiniz `DBG_NEW` . Hata ayıklama yapılarında, `DBG_NEW` `operator new` blok türü, dosya ve satır numarası için ek parametreler alan küresel bir aşırı yüklemesi kullanır. `new` `_malloc_dbg` Ek bilgileri kaydetmek için çağrıların aşırı yüklemesi. Bellek sızıntısı raporlarında, sızdırılan nesnelerin ayrıldığı dosya adı ve satır numarası gösterilir. Yayın derlemeleri hala varsayılanı kullanır `new` . Aşağıda bir teknik örnek verilmiştir:

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

bu kodu Visual Studio hata ayıklayıcısında çalıştırdığınızda, öğesine yapılan çağrı `_CrtDumpMemoryLeaks` **çıkış** penceresinde şuna benzer bir rapor oluşturur:

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
>Adlı bir önişlemci makrosu `new` veya başka bir dil anahtar sözcüğü oluşturmanız önerilmez.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Bir bellek ayırma numarasında kesme noktaları ayarlayın

Bellek ayırma numarası, bir sızdırılan bellek bloğu ayrıldığında size bildirir. 16. bellek ayırma numarasına sahip bir blok, örneğin, uygulamanın çalıştırılması sırasında ayrılan belleğin 18of bloğu olur. CRT raporu, çalışma sırasında, CRT kitaplığı ve MFC gibi diğer kitaplıkların ayırmaları dahil tüm bellek bloğu ayırmalarını sayar. Bu nedenle, bellek ayırma blok numarası 18 muhtemelen kodunuz tarafından ayrılan bir 18 bellek bloğu değildir.

Ayırma numarasını, bellek ayırmada bir kesme noktası ayarlamak için kullanabilirsiniz.

**İzleme penceresi kullanarak bir bellek ayırma kesme noktası ayarlamak için:**

1. Uygulamanızın başlangıcına yakın bir kesme noktası ayarlayın ve hata ayıklamayı başlatın.

1. uygulama kesme noktasında durakladığında, **hata ayıkla** Windows izleme 1 ' i seçerek bir **izleme** penceresi açın  >    >   (veya **2**. **izleyin** veya **4**. izleyin).

1. **Gözcü** penceresinde `_crtBreakAlloc` **ad** sütununu yazın.

   CRT kitaplığının çok iş parçacıklı DLL sürümünü (/MD seçeneği) kullanıyorsanız, bağlam işlecini ekleyin: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Hata ayıklama simgelerinin yüklendiğinden emin olun. Aksi takdirde `_crtBreakAlloc` , *tanımlanamayan* olarak bildirilir.

1.  **Enter** tuşuna basın.

   Hata ayıklayıcı çağrıyı değerlendirir ve sonucu **değer** sütununa koyar. Bellek ayırmaları üzerinde herhangi bir kesme noktası ayarlanmamışsa bu değer **-1** olacaktır.

1. **Değer** sütununda, değeri hata ayıklayıcının kesilmesini istediğiniz bellek ayırmasının ayırma numarasıyla değiştirin.

Bir bellek ayırma numarasında bir kesme noktası ayarladıktan sonra, hata ayıklamaya devam edin. Aynı koşulların altında çalıştığından emin olun, böylece bellek ayırma numarası değişmez. Programınız belirtilen bellek ayırmaya kesildiğinde, belleğin ayrıldığı koşulları öğrenmek için **çağrı yığını** penceresini ve diğer hata ayıklama pencerelerini kullanın. Daha sonra, nesneye ne olduğunu gözlemlemek ve neden düzgün şekilde serbest bırakılmadığını belirlemek için yürütmeye devam edebilirsiniz.

Nesne üzerinde bir veri kesme noktası ayarlanması da yararlı olabilir. Daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

Ayrıca, kodda bellek ayırma kesme noktaları da ayarlayabilirsiniz. Şunları yapabilirsiniz:

```cpp
_crtBreakAlloc = 18;
```

 veya:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Bellek durumlarını karşılaştırın

Bellek sızıntılarını bulmaya yönelik başka bir teknik, anahtar noktalarında uygulamanın bellek durumunun anlık görüntülerini almayı içerir. Uygulamanızdaki belirli bir noktada bellek durumunun anlık görüntüsünü almak için bir `_CrtMemState` Yapı oluşturun ve `_CrtMemCheckpoint` işleve geçirin.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint`İşlevi, yapıyı geçerli bellek durumunun bir anlık görüntüsüyle doldurur.

Bir yapının içeriğini çıkarmak için `_CrtMemState` yapıyı `_ CrtMemDumpStatistics` işleve geçirin:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` aşağıdaki gibi görünen bellek durumunun dökümünü verir:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Bir kod bölümünde bellek sızıntısı oluşup oluşmadığını anlamak için, bölümden önce ve sonra bellek durumunun anlık görüntülerini alabilir ve ardından `_ CrtMemDifference` iki durumu karşılaştırmak için ' ı kullanabilirsiniz:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` bellek durumlarını karşılaştırır ve `s1` , `s2` `s3` ve arasındaki fark olan () içinde bir sonuç döndürür `s1` `s2` .

Bellek sızıntılarını bulmak için bir teknik `_CrtMemCheckpoint` , uygulamanızın başlangıcında ve sonunda çağrılar yerleştirip `_CrtMemDifference` sonuçları karşılaştırmak için kullanarak başlar. `_CrtMemDifference`Bir bellek sızıntısı gösteriyorsa, `_CrtMemCheckpoint` sızıntı kaynağını yalıtana kadar programınızı bir ikili arama kullanarak bölmek için daha fazla çağrı ekleyebilirsiniz.

## <a name="false-positives"></a>Hatalı pozitif sonuçlar

 `_CrtDumpMemoryLeaks` bir kitaplık, iç ayırmaları CRT blokları veya istemci blokları yerine normal bloklar olarak işaretlerse, bellek sızıntılarına ilişkin hatalı göstergeler verebilir. Bu durumda, `_CrtDumpMemoryLeaks` Kullanıcı ayırmaları ve iç kitaplık ayırmaları arasındaki farkı söylemez. Kitaplık ayırmaları için genel Yıkıcılar, çağırdığınız noktadan sonra çalışıyorsa `_CrtDumpMemoryLeaks` , her iç kitaplık ayırması bir bellek sızıntısı olarak bildirilir. standart şablon kitaplığının Visual Studio .net sürümünden önceki sürümleri, `_CrtDumpMemoryLeaks` bu tür hatalı pozitif durumları raporlamayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [CRT hata ayıklama öbeği ayrıntıları](../debugger/crt-debug-heap-details.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
