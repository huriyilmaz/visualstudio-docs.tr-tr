---
title: CRT kitaplığını kullanarak bellek sızıntılarını bulma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 831cae8d83bc26e05b80d6948a3168a6e6a387c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682430"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>CRT Kitaplığını Kullanarak Bellek Sızıntılarını Bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha önce ayrılan belleği doğru serbest bırakma hatası olarak tanımlanan bellek sızıntıları, C/C++ uygulamalarında en hafif ve algılayan hata hataları arasındadır. Küçük bir bellek sızıntısı ilk başta fark olmayabilir, ancak zaman içinde, aşamalı bir bellek sızıntısı, uygulamanın belleği tükendiği zaman performansın azalmasına neden olan belirtilerden kaynaklanabilir. Tüm kullanılabilir belleği kullanan bir sızan uygulama, başka bir uygulamanın kilitlenmesine neden olabilir ve bu da uygulamanın sorumlu olduğu konusunda karışıklık oluşturur. Hatta, oluşabilecek zararsız bellek sızıntıları, düzeltilmesi gereken diğer sorunların sentomatik olması olabilir.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı ve C çalışma zamanı (CRT) kitaplıkları, bellek sızıntılarını tespit etmek ve tanımlamak için kullanabileceğiniz yolları sağlar.  
  
## <a name="enabling-memory-leak-detection"></a>Bellek sızıntısı algılamayı etkinleştirme  
 Bellek sızıntılarını algılamaya yönelik birincil araçlar, hata ayıklayıcı ve C çalışma zamanı kitaplıkları (CRT) hata ayıklama yığını işlevleridir.  
  
 Hata ayıklama yığını işlevlerini etkinleştirmek için, programınıza aşağıdaki deyimleri ekleyin:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 CRT işlevlerinin düzgün çalışması için `#include` deyimlerin burada gösterilen sırayı izlemesi gerekir.  
  
 Crtdbg. h dahil olmak üzere, `malloc` ve [ücretsiz](https://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) işlevleri, [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) ve `free` , bellek ayırmayı ve ayırmayı kaldırma işlemlerini izleyen hata ayıklama sürümleriyle eşler. Bu eşleme yalnızca, içeren hata ayıklama yapılarında oluşur `_DEBUG` . Yayın derlemeleri normal `malloc` ve işlevleri kullanır `free` .  
  
 `#define`İfade, CRT yığın işlevlerinin temel bir sürümünü karşılık gelen hata ayıklama sürümüne eşler. `#define`İfadeyi atlarsanız, bellek sızıntısı dökümü daha az ayrıntılı olacaktır.  
  
 Bu deyimleri kullanarak hata ayıklama yığın işlevlerini etkinleştirdikten sonra, uygulamanız `_CrtDumpMemoryLeaks` çıktığında bir bellek sızıntısı raporu göstermek için bir uygulama çıkış noktasına bir çağrı yerleştirebilirsiniz:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Uygulamanızda birden çok çıkış varsa, her çıkış noktasında [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) el ile bir çağrı yerleştirmeniz gerekmez. Uygulamanızın başlangıcında öğesine yapılan bir çağrı `_CrtSetDbgFlag` , `_CrtDumpMemoryLeaks` her çıkış noktasında otomatik çağrıya neden olur. Burada gösterilen iki bit alanını ayarlamanız gerekir:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Varsayılan olarak, `_CrtDumpMemoryLeaks` **Çıkış** penceresinin **hata ayıklama** bölmesine bellek sızıntısı raporunu verir. `_CrtSetReportMode`Raporu başka bir konuma yönlendirmek için ' i kullanabilirsiniz.  
  
 Bir kitaplık kullanıyorsanız, kitaplık çıktıyı başka bir konuma sıfırlayabilir. Bu durumda, burada gösterildiği gibi çıkış konumunu **Çıkış** penceresine geri getirebilirsiniz:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Bellek sızıntısı raporunu yorumlama  
 Uygulamanız tanımlanmıyorsa `_CRTDBG_MAP_ALLOC` [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) aşağıdaki gibi görünen bir bellek sızıntısı raporu görüntüler:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Uygulamanız tanımlıyorsa `_CRTDBG_MAP_ALLOC` , bellek sızıntısı raporu şöyle görünür:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Fark, ikinci raporun dosyanın adını ve sızdırılan belleğin ilk ayrıldığı satır numarasını gösterdiği yerdir.  
  
 Sizin tanımladığınız `_CRTDBG_MAP_ALLOC` veya etmeksizin, bellek sızıntısı raporu aşağıdaki bilgileri görüntüler:  
  
- Bu örnekteki bellek ayırma numarası `18`  
  
- Bu örnekteki [blok türü](https://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97) `normal` .  
  
- Bu örnekteki onaltılık bellek konumu `0x00780E80` .  
  
- `64 bytes`Bu örnekteki bloğun boyutu.  
  
- Blok içindeki ilk 16 baytlık veriler, onaltılık biçimde.  
  
  Bellek sızıntısı raporu, bir bellek bloğunu normal, istemci veya CRT olarak tanımlar. *Normal bir blok* , programınız tarafından ayrılan sıradan bellektir. *İstemci bloğu* , MFC programları tarafından yıkıcı gerektiren nesneler için kullanılan özel bir bellek bloğu türüdür. MFC `new` işleci, oluşturulmakta olan nesneye uygun şekilde normal bir blok veya bir istemci bloğu oluşturur. CRT *bloğu* , kendi kullanımı için CRT kitaplığı tarafından ayrılır. CRT kitaplığı, bu bloklar için ayırmayı kaldırma işler. Bu nedenle, önemli ölçüde yanlış bir şey olmadığı takdirde, CRT kitaplığı bozuk olduğu müddetçe bellek sızıntısı raporunda bunları görmemiz çok düşüktür.  
  
  Bellek sızıntısı raporlarında hiçbir şekilde görünmeyen iki tür bellek bloğu vardır. *Serbest bir blok* , yayınlanan bellektir. Yani, tanım olarak sızmaz. *Yoksayma bloğu* , bellek sızıntısı raporundan hariç tutmak için açıkça işaretlediğiniz bellektir.  
  
  Bu teknikler, standart CRT işlevi kullanılarak ayrılan bellek için çalışır `malloc` . Programınız, C++ işlecini kullanarak bellek ayırırsa `new` , yalnızca `operator new` bellek sızıntısı raporundaki genel çağrıların uygulanması durumunda dosya ve satır numarasını görebilirsiniz `_malloc_dbg` . Bu davranış çok faydalı olmadığından, aşağıdaki gibi görünen bir makro kullanarak ayırmayı yapan satırı raporlamak için bunu değiştirebilirsiniz: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Artık `new` kodunuzda makroyu kullanarak işleci değiştirebilirsiniz `DBG_NEW` . Hata ayıklama yapılarında, bu, `operator new` blok türü, dosya ve satır numarası için ek parametreler alan küresel bir aşırı yüklemesi kullanır. `new` `_malloc_dbg` Ek bilgileri kaydetmek için çağrıların bu aşırı yüklemesi. Kullandığınızda `DBG_NEW` , bellek sızıntısı raporları, sızdırılan nesnelerin ayrıldığı dosya adını ve satır numarasını gösterir. Perakende Derlemeleriyle, varsayılan kullanır `new` . (Veya başka bir dil anahtar sözcüğü adlı bir önişlemci makrosu oluşturmanızı önermiyoruz `new` .) Aşağıda bir teknik örnek verilmiştir:  
  
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
  
Bu kodu Visual Studio 'da hata ayıklayıcıda çalıştırdığınızda, ' `_CrtDumpMemoryLeaks` a çağrı **Çıkış** penceresinde şuna benzer bir rapor oluşturur:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Bu size, sızdırılan ayırmanın debug_new. cpp için 20. satırdaki olduğunu söyler.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Bir bellek ayırma numarasında kesme noktaları ayarlama  
 Bellek ayırma numarası, bir sızdırılan bellek bloğu ayrıldığında size bildirir. 16. bellek ayırma numarası 18 olan bir blok, örneğin, uygulamanın çalıştırılması sırasında ayrılan belleğin 18. bloğu olur. CRT raporu, çalıştırma sırasında tüm bellek bloğu ayırmalarını sayar. Buna CRT kitaplığı ve MFC gibi diğer kitaplıkların ayırmaları dahildir. Bu nedenle, bellek ayırma numarası 18 olan bir blok, kodunuz tarafından ayrılan bir 18 bellek bloğu olmayabilir. Genellikle, bu olmayacaktır.  
  
 Ayırma numarasını, bellek ayırmada bir kesme noktası ayarlamak için kullanabilirsiniz.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>izleme penceresi kullanarak bir bellek ayırma kesme noktası ayarlamak için  
  
1. Uygulamanızın başlangıcına yakın bir kesme noktası ayarlayın ve uygulamanızı başlatın.  
  
2. Uygulama kesme noktasında kesildiğinde, **Gözcü** penceresi.  
  
3. **Gözcü** penceresinde `_crtBreakAlloc` **ad** sütununu yazın.  
  
    CRT kitaplığının çok iş parçacıklı DLL sürümünü (/MD seçeneği) kullanıyorsanız, bağlam işlecini dahil edin: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. **Return**tuşuna basın.  
  
    Hata ayıklayıcı çağrıyı değerlendirir ve sonucu **değer** sütununa koyar. Bellek ayırmaları üzerinde herhangi bir kesme noktası ayarlanmamışsa bu değer – 1 olacaktır.  
  
5. **Değer** sütununda, gösterilen değeri, bölmek istediğiniz bellek ayırmasının ayırma numarasıyla değiştirin.  
  
   Bir bellek ayırma numarasında bir kesme noktası ayarladıktan sonra, hata ayıklamaya devam edebilirsiniz. Bellek ayırma sırasının değişmemesi için programı önceki çalıştırmaya göre aynı koşullarda çalıştırmaya dikkat edin. Programınız belirtilen bellek ayırmaya kesildiğinde, belleğin ayrıldığı koşulları öğrenmek için **çağrı yığını** penceresini ve diğer hata ayıklama pencerelerini kullanabilirsiniz. Daha sonra, nesneye ne olduğunu gözlemlemek ve neden düzgün şekilde serbest bırakılmadığını belirlemek için yürütmeye devam edebilirsiniz.  
  
   Nesne üzerinde bir veri kesme noktası ayarlanması da yararlı olabilir. Daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).  
  
   Ayrıca, kodda bellek ayırma kesme noktaları da ayarlayabilirsiniz. Bunu yapmak için iki yol vardır:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 veya:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Bellek durumlarını karşılaştırma  
 Bellek sızıntılarını bulmaya yönelik başka bir teknik, anahtar noktalarında uygulamanın bellek durumunun anlık görüntülerini almayı içerir. Uygulamanızdaki belirli bir noktada bellek durumunun anlık görüntüsünü almak için bir **_CrtMemState** yapısı oluşturun ve `_CrtMemCheckpoint` işleve geçirin. Bu işlev, yapıyı geçerli bellek durumunun bir anlık görüntüsüyle doldurur:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` yapıyı, geçerli bellek durumunun bir anlık görüntüsüyle doldurur.  
  
 **_CrtMemState** yapısının içeriğini çıkarmak için yapıyı `_ CrtMemDumpStatistics` işleve geçirin:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` aşağıdaki gibi görünen bellek durumunun dökümünü verir:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Bir kod bölümünde bellek sızıntısı oluşup oluşmadığını anlamak için, bölümden önce ve sonra bellek durumunun anlık görüntülerini alabilir ve ardından `_ CrtMemDifference` iki durumu karşılaştırmak için ' ı kullanabilirsiniz:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` , ve arasındaki fark olan bellek durumlarını karşılaştırır ve `s1` `s2` () içinde bir sonuç döndürür `s3` `s1` `s2` .  
  
 Bellek sızıntılarını bulmak için bir teknik `_CrtMemCheckpoint` , uygulamanızın başlangıcında ve sonunda çağrılar yerleştirip `_CrtMemDifference` sonuçları karşılaştırmak için kullanarak başlar. `_CrtMemDifference`Bir bellek sızıntısı gösteriyorsa, `_CrtMemCheckpoint` sızıntı kaynağını yalıtana kadar programınızı bir ikili arama kullanarak bölmek için daha fazla çağrı ekleyebilirsiniz.  
  
## <a name="false-positives"></a>Hatalı pozitif sonuçlar  
 Bazı durumlarda, `_CrtDumpMemoryLeaks` bellek sızıntıları için yanlış göstergeler verebilir. İç ayırmaları s veya s yerine _NORMAL_BLOCKs olarak işaretleyen bir kitaplık kullanırsanız bu durum oluşabilir `_CRT_BLOCK` `_CLIENT_BLOCK` . Bu durumda, `_CrtDumpMemoryLeaks` Kullanıcı ayırmaları ve iç kitaplık ayırmaları arasındaki farkı söylemez. Kitaplık ayırmaları için genel Yıkıcılar, çağırdığınız noktadan sonra çalışıyorsa `_CrtDumpMemoryLeaks` , her iç kitaplık ayırması bir bellek sızıntısı olarak bildirilir. Standart Şablon kitaplığı, Visual Studio .NET sürümünden önceki eski sürümleri, `_CrtDumpMemoryLeaks` Bu tür hatalı pozitif sonuçları raporlamayabilirdi ancak bu, son sürümlerde düzeltildi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama yığın ayrıntıları](../debugger/crt-debug-heap-details.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
