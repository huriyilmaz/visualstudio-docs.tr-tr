---
title: MFC hata ayıklama teknikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c795e978de3911b3c5e815583c32e878fd7b173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696908"
---
# <a name="mfc-debugging-techniques"></a>MFC Hata Ayıklama Teknikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MFC programında hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [TRACE makrosu](#BKMK_The_TRACE_macro)  
  
 [MFC 'de bellek sızıntılarını algılama](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Bellek ayırmalarını izleme](#BKMK_Tracking_memory_allocations)  
  
- [Bellek tanılamayı etkinleştirme](#BKMK_Enabling_memory_diagnostics)  
  
- [Bellek anlık görüntülerini alma](#BKMK_Taking_memory_snapshots)  
  
- [Bellek istatistiklerini görüntüleme](#BKMK_Viewing_memory_statistics)  
  
- [Nesne dökümlerini alma](#BKMK_Taking_object_dumps)  
  
  - [Bellek dökümlerini yorumlama](#BKMK_Interpreting_memory_dumps)  
  
  - [Nesne dökümlerini özelleştirme](#BKMK_Customizing_object_dumps)  
  
    [MFC hata ayıklama derlemesinin boyutunu azaltma](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Seçilen modüller için hata ayıklama bilgileriyle bir MFC uygulaması oluşturma](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC, kaynak kodundaki sabit kodlama kesme noktaları için özel bir [AfxDebugBreak](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) işlevi sağlar:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Intel platformlarında, `AfxDebugBreak` çekirdek kodu yerine kaynak kodu kesen aşağıdaki kodu üretir:  
  
```  
_asm int 3  
```  
  
 Diğer platformlarda `AfxDebugBreak` yalnızca çağırır `DebugBreak` .  
  
 `AfxDebugBreak`Bir yayın derlemesi oluştururken veya çevrelemek için kullandığınızda deyimleri kaldırmayı unutmayın `#ifdef _DEBUG` .  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> TRACE makrosu  
 Hata ayıklayıcı [çıktı penceresinde](../ide/reference/output-window.md)programınızdaki iletileri göstermek Için, [ATLTRACE](https://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) makrosunu veya MFC [Trace](https://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) makrosunu kullanabilirsiniz. [Onaylamalar](../debugger/c-cpp-assertions.md)gibi, izleme makroları yalnızca programınızın hata ayıklama sürümünde etkindir ve yayın sürümünde derlendiğinde kaybolur.  
  
 Aşağıdaki örneklerde, **izleme** makrosunu kullanabileceğiniz bazı yollar gösterilmektedir. Benzer şekilde `printf` , **Trace** makrosu bir dizi bağımsız değişkeni işleyebilir.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 TRACE makrosu hem char * hem de wchar_t parametrelerini uygun şekilde işler \* . Aşağıdaki örneklerde, farklı dize parametresi türleriyle birlikte Izleme makrosunun kullanımı gösterilmektedir.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 **İzleme** makrosu hakkında daha fazla bilgi için bkz. [Tanılama Hizmetleri](https://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> MFC 'de bellek sızıntılarını algılama  
 MFC, ayrılan ancak serbest bırakılmakta olan belleği algılamaya yönelik sınıfları ve işlevleri sağlar.  
  
### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Bellek ayırmalarını izleme  
 MFC 'de, bellek sızıntılarını bulmaya yardımcı olması için **Yeni** işlecin yerine makro [DEBUG_NEW](https://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) kullanabilirsiniz. Programınızın hata ayıklama sürümünde, `DEBUG_NEW` ayırdığı her bir nesne için dosya adını ve satır numarasını izler. Programınızın bir yayın sürümünü derlerken `DEBUG_NEW` dosya adı ve satır numarası bilgisi olmadan basit bir **Yeni** işlem olarak çözümlenir. Bu nedenle, programınızın yayın sürümünde hiçbir hızda ceza puanı ödeyin.  
  
 Yeni bir yerde kullanmak üzere tüm programınızı yeniden yazmak istemiyorsanız `DEBUG_NEW` , bu makroyu kaynak dosyalarınızda **new**tanımlayabilirsiniz:  
  
```  
#define new DEBUG_NEW  
```  
  
 Bir [nesne dökümü](#BKMK_Taking_object_dumps)gerçekleştirdiğinizde, ile ayrılan her bir nesne, `DEBUG_NEW` ayrılan dosya ve satır numarasını gösterir ve bellek sızıntıları kaynaklarını bulmanızı sağlar.  
  
 MFC çerçevesinin hata ayıklama sürümü `DEBUG_NEW` otomatik olarak kullanır, ancak kodunuz değildir. Avantajlarından yararlanmak istiyorsanız `DEBUG_NEW` , `DEBUG_NEW` yukarıda gösterildiği gibi açıkça veya **#define yeni** kullanmanız gerekir.  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Bellek tanılamayı etkinleştirme  
 Bellek Tanılama tesislerini kullanabilmeniz için, tanılama izlemeyi etkinleştirmeniz gerekir.  
  
 **Bellek tanılamayı etkinleştirmek veya devre dışı bırakmak için**  
  
- Tanılama bellek ayırıcısını etkinleştirmek veya devre dışı bırakmak için [Afxenablememoryıtracking](https://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) genel işlevini çağırın. Bellek Tanılama, hata ayıklama kitaplığı 'nda varsayılan olarak açık olduğundan, genellikle bu işlevi, program yürütme hızını artıran ve tanılama çıkışını azaltan, geçici olarak devre dışı bırakmak için kullanacaksınız.  
  
  **AfxMemDF ile belirli bellek tanılama özelliklerini seçmek için**  
  
- Bellek tanılama özellikleri üzerinde daha kesin bir denetim istiyorsanız, [afxMemDF](https://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086)MFC genel değişkeninin değerini ayarlayarak, tek tek Bellek Tanılama özelliklerini seçmeli şekilde açıp kapatabilirsiniz. Bu değişken, sıralanmış tür **afxMemDF**tarafından belirtilen şekilde aşağıdaki değerlere sahip olabilir.  
  
  |Değer|Açıklama|  
  |-----------|-----------------|  
  |**allocMemDF**|Tanılama belleği ayırıcısını açın (varsayılan).|  
  |**delayFreeMemDF**|Çağırma sırasında `delete` veya `free` Program kapatılıncaya kadar bellek boşaltmayı geciktir. Bu, programınızın mümkün olan en yüksek miktarda belleği ayırmasına neden olur.|  
  |**Checkalwaykokmdf**|Bellek ayrıldığı veya serbest bırakılmış her seferinde [AfxCheckMemory](https://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) çağrısı yapın.|  
  
   Bu değerler, burada gösterildiği gibi mantıksal veya işlem gerçekleştirerek birlikte kullanılabilir:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [Bu konuda](#BKMK_In_this_topic)  
  
### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Bellek anlık görüntülerini alma  
  
1. Bir [CMemoryState](https://msdn.microsoft.com/8fade6e9-c6fb-4b2a-8565-184a912d26d2) nesnesi oluşturun ve [CMemoryState:: Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) üye işlevini çağırın. Bu, ilk bellek anlık görüntüsünü oluşturur.  
  
2. Programınız bellek ayırmayı ve ayırmayı kaldırma işlemlerini gerçekleştirdikten sonra, `CMemoryState` Bu nesne için başka bir nesne ve çağrı oluşturun `Checkpoint` . Bu, bellek kullanımının ikinci bir anlık görüntüsünü alır.  
  
3. Üçüncü bir `CMemoryState` nesne oluşturun ve [CMemoryState::D ifference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) üye işlevini çağırın ve bu iki önceki nesne bağımsız değişken olarak sağlama `CMemoryState` . İki bellek durumu arasında bir fark varsa, `Difference` işlev sıfır dışında bir değer döndürür. Bu, bazı bellek bloklarının serbest bırakılmadığını gösterir.  
  
    Bu örnekte kodun nasıl göründüğü gösterilmektedir:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Bellek denetleme deyimlerinin, `#ifdef` [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) /  yalnızca programınızın hata ayıklama sürümlerinde derlenmesi için _DEBUG **#endif** blokları tarafından parantez içine alınmış olduğuna dikkat edin.  
  
    Artık bir bellek sızıntısı olduğunu öğrenmiş olduğunuza göre, diğer bir üye işlevi olan [CMemoryState::D Fertime istatistiklerini](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) bulmanıza yardımcı olacak şekilde kullanabilirsiniz.  
  
   [Bu konuda](#BKMK_In_this_topic)  
  
### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Bellek istatistiklerini görüntüleme  
 [CMemoryState::D ifference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) işlevi iki bellek durumu nesnesine bakar ve başlangıç ve bitiş durumları arasında yığından serbest bırakılmayan nesneleri algılar. Bellek anlık görüntülerini aldıktan ve kullanarak bunları karşılaştırdıktan sonra `CMemoryState::Difference` , serbest bırakılmayan nesneler hakkında bilgi almak Için [CMemoryState::D öncelik istatistiklerini](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) çağırabilirsiniz.  
  
 Aşağıdaki örneği inceleyin:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Örnekteki örnek bir döküm şöyle görünür:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Serbest bloklar, olarak ayarlandıysa, ayırmayı kaldırma geciktirilen bloklardır `afxMemDF` `delayFreeMemDF` .  
  
 İkinci satırda gösterilen sıradan nesne blokları, yığında ayrılmaya devam eder.  
  
 Nesne olmayan bloklar, ile ayrılmış dizileri ve yapıları içerir `new` . Bu durumda, yığında dört nesne olmayan blok ayrılmıştı ancak serbest bırakılmamalıdır.  
  
 `Largest number used` program tarafından herhangi bir zamanda kullanılan en fazla bellek sayısını verir.  
  
 `Total allocations` program tarafından kullanılan toplam bellek miktarını verir.  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Nesne dökümlerini alma  
 Bir MFC programında, yığın üzerinde serbest bırakılmayan tüm nesnelerin bir açıklamasının dökümünü almak için [CMemoryState::D umpallobjectssince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) kullanabilirsiniz. `DumpAllObjectsSince` Son [CMemoryState:: Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a)öğesinden bu yana ayrılan tüm nesneleri döker. Hiçbir `Checkpoint` çağrı gerçekleşmiyor ise, `DumpAllObjectsSince` tüm nesneleri ve şu anda bellekte olmayan nesneleri döker.  
  
> [!NOTE]
> MFC nesne dökümünü kullanabilmeniz için, [Tanılama izlemeyi etkinleştirmeniz](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_memory_diagnostics)gerekir.  
  
> [!NOTE]
> MFC, programınız çıktığında tüm sızdırılan nesneleri otomatik olarak döker, bu nedenle bu noktada nesnelerin dökümünü yapmak için kod oluşturmanız gerekmez.  
  
 Aşağıdaki kod, iki bellek durumunu karşılaştırarak bir bellek sızıntısını sınar ve bir sızıntı algılanırsa tüm nesneleri döker.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Döküm içeriği şöyle görünür:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Çoğu satır başındaki küme ayraçları içindeki sayılar, nesnelerin ayrıldığı sırayı belirtir. En son ayrılan nesne en yüksek sayıya sahiptir ve dökümün en üstünde görünür.  
  
 Bir nesne dökümünden en fazla bilgi miktarını almak için, `Dump` `CObject` nesne dökümünü özelleştirmek üzere herhangi bir türetilmiş nesnenin üye işlevini geçersiz kılabilirsiniz.  
  
 Genel değişkeni, `_afxBreakAlloc` küme ayraçları içinde gösterilen sayı olarak ayarlayarak belirli bir bellek ayırma üzerinde bir kesme noktası ayarlayabilirsiniz. Programı yeniden çalıştırırsanız, bu ayırma gerçekleştiğinde hata ayıklayıcı yürütmeyi keser. Ardından, programınızın bu noktaya nasıl kullanıldığını görmek için çağrı yığınına bakabilirsiniz.  
  
 C çalışma zamanı kitaplığı, C çalışma zamanı ayırmaları için kullanabileceğiniz benzer bir işleve sahiptir [_CrtSetBreakAlloc](https://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1).  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Bellek dökümlerini yorumlama  
 Daha ayrıntılı bilgi için bu nesne dökümünden bakın:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Bu dökümü oluşturan program, yığın üzerinde diğeri yığın üzerinde olmak üzere yalnızca iki açık ayırmaya sahipti:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson`Oluşturucu, `char` üye değişkenlerini başlatmak için kullanılan işaretçiler olan üç bağımsız değişken alır `CString` . Bellek dökümünde, `CPerson` nesneyi üç nesne olmayan blok (3, 4 ve 5) ile birlikte görebilirsiniz. Bunlar `CString` üye değişkenlerinin karakterlerini tutar ve `CPerson` nesne yıkıcısı çağrıldığında silinmez.  
  
 Blok numarası 2 `CPerson` nesnenin kendisidir. `$51A4` bloğunun adresini temsil eder ve öğesinden sonra, `CPerson` `Dump` [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2)tarafından çağrıldığında::.  
  
 `CString`Çerçeve değişkeninde karakter sayısıyla eşleşen sıra numarası ve boyutu nedeniyle, 1 blok numarası çerçeve değişkeniyle ilişkili olduğunu tahmin edebilirsiniz `CString` . Çerçeve kapsam dışına geçtiğinde çerçevede ayrılan değişkenler otomatik olarak serbest bırakılır.  
  
 **Çerçeve değişkenleri**  
  
 Genel olarak, çerçeve değişkenleri kapsam dışına dönerek serbest bırakıldıklarından, çerçeve değişkenleriyle ilişkili yığın nesneleri hakkında endişelenmemelisiniz. Bellek Tanılama dökümlerinizin dağınıklığını önlemek için, çağrılarınızı `Checkpoint` çerçeve değişkenlerinin kapsamı dışında olacak şekilde konumlandırmalısınız. Örneğin, aşağıda gösterildiği gibi, önceki ayırma kodunun etrafına kapsam ayraçları yerleştirin:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Kapsam ayraçları yerine, bu örnek için bellek dökümü aşağıdaki gibidir:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Nesne olmayan ayırmalar**  
  
 Bazı ayırmaların nesneler (gibi `CPerson` ) ve bazıları ise nesne olmayan ayırmalar olduğunu unutmayın. "Nesne olmayan ayırmalar" `CObject` ,, ya da Long gibi temel C türlerinden türetilmeyen veya ayırmayan nesnelere yönelik ayırmalarda bulunur `char` `int` . **long** **CObject ile**türetilmiş sınıf, iç arabellekler gibi ek alan ayırırsa, bu nesneler hem nesne hem de nesne olmayan ayırmaları gösterir.  
  
 **Bellek sızıntılarını önlemek**  
  
 Yukarıdaki kodda, çerçeve değişkeniyle ilişkili bellek bloğunun `CString` otomatik olarak serbest bırakılmış olduğunu ve bellek sızıntısı olarak gösterilmediğine dikkat edin. Kapsam kurallarıyla ilişkili otomatik ayırmayı kaldırma, çerçeve değişkenleriyle ilişkili çoğu bellek sızıntılarını üstlenir.  
  
 Ancak yığında ayrılan nesneler için, bir bellek sızıntısını engellemek için nesneyi açıkça silmeniz gerekir. Önceki örnekte yer alan son bellek sızıntısını temizlemek için, `CPerson` yığında ayrılan nesneyi aşağıdaki gibi silin:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Nesne dökümlerini özelleştirme  
 [CObject](https://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a)'ten bir sınıf türettiğinizde, `Dump` nesneleri [Çıkış penceresinde](../ide/reference/output-window.md)dökmek için [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) kullandığınızda ek bilgi sağlamak için üye işlevini geçersiz kılabilirsiniz.  
  
 `Dump`İşlevi, bir döküm bağlamına ([CDumpContext](https://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)) nesnenin üye değişkenlerinin metinsel bir gösterimini yazar. Döküm bağlamı bir g/ç akışına benzer. ' **<<** A veri göndermek için ekleme işlecini () kullanabilirsiniz `CDumpContext` .  
  
 İşlevi geçersiz kıldığınızda `Dump` , `Dump` temel sınıf nesnesinin içeriğinin dökümünü yapmak için önce temel sınıf sürümünü çağırmanız gerekir. Ardından, türetilmiş sınıfınızın her bir üye değişkeni için bir metinsel açıklama ve değer çıkışı yapın.  
  
 İşlevin bildirimi şöyle `Dump` görünür:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Nesne dökümü yalnızca programınızda hata ayıklaması yaparken anlamlı hale geldiğinde, `Dump` işlevin bildirimi **#ifdef _DEBUG/#endif** bloğu ile parantez içine alınmıştır.  
  
 Aşağıdaki örnekte, `Dump` işlevi önce `Dump` temel sınıfının işlevini çağırır. Ardından, her üye değişkeninin kısa bir açıklamasını ve üyenin değerini tanılama akışına yazar.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 `CDumpContext`Döküm çıkışının nereye gidebileceği belirtmek için bir bağımsız değişken sağlamanız gerekir. MFC 'nin hata ayıklama sürümü, `CDumpContext` `afxDump` hata ayıklayıcıya çıktı gönderen adlı önceden tanımlanmış bir nesne sağlar.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [Bu konuda](#BKMK_In_this_topic)  
  
## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> MFC hata ayıklama derlemesinin boyutunu azaltma  
 Büyük bir MFC uygulaması için hata ayıklama bilgileri çok miktarda disk alanı alabilir. Boyutunu azaltmak için şu yordamlardan birini kullanabilirsiniz:  
  
1. /Z7 yerine [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) SEÇENEĞINI kullanarak MFC kitaplıklarını yeniden derleyin **.** Bu seçenekler, tüm kitaplık için hata ayıklama bilgilerini içeren tek bir program veritabanı (PDB) dosyası oluşturur, artıklığı azaltır ve alan tasarrufu yapın.  
  
2. MFC kitaplıklarını hata ayıklama bilgileri olmadan yeniden derleyin ( [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) seçeneği). Bu durumda, hata ayıklama bilgilerinin bulunmaması, MFC kitaplık kodu içindeki çoğu hata ayıklayıcı tesislerini kullanmanızı önler, ancak MFC kitaplıklarının zaten kapsamlı bir şekilde ayıklandığından bu sorun olmayabilir.  
  
3. Aşağıda açıklandığı gibi, seçilen modüller için hata ayıklama bilgileri ile kendi uygulamanızı oluşturun.  
  
   [Bu konuda](#BKMK_In_this_topic)  
  
### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Seçilen modüller için hata ayıklama bilgileriyle bir MFC uygulaması oluşturma  
 MFC hata ayıklama kitaplıklarıyla seçili modüllerin oluşturulması, bu modüllerde adımlamayı ve diğer hata ayıklama olanaklarını kullanmanıza olanak sağlar. Bu yordam, Visual C++ Makefile 'ın hata ayıklama ve yayın modlarını kullanır, bu nedenle aşağıdaki adımlarda açıklanan değişiklikleri tasarımda (ve ayrıca tam bir yayın derlemesi gerektiğinde "tümünü yeniden derle" seçeneğini oluşturur).  
  
1. Çözüm Gezgini, projeyi seçin.  
  
2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.  
  
3. İlk olarak yeni bir proje yapılandırması oluşturacaksınız.  
  
   1. ** \<Project> Özellik sayfaları** iletişim kutusunda **Configuration Manager** düğmesine tıklayın.  
  
   2. [Configuration Manager iletişim kutusunda](https://msdn.microsoft.com/fa182dca-282e-4ae5-bf37-e155344ca18b), kılavuzdaki projenizi bulun. **Yapılandırma** sütununda, öğesini seçin **\<New...>** .  
  
   3. [Yeni proje yapılandırması iletişim kutusunda](https://msdn.microsoft.com/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), yeni yapılandırmanız Için, **Proje yapılandırma adı** kutusuna "kısmi hata ayıklama" gibi bir ad yazın.  
  
   4. **Ayarları Şuradan Kopyala** listesinden **yayın**' ı seçin.  
  
   5. **Yeni proje yapılandırması**iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
   6. **Configuration Manager** iletişim kutusunu kapatın.  
  
4. Şimdi tüm projenin seçeneklerini ayarlayacaksınız.  
  
   1. **Özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörü altında **genel** kategorisini seçin.  
  
   2. Proje ayarları kılavuzunda, **Proje Varsayılanları** ' nı genişletin (gerekirse).  
  
   3. **Proje Varsayılanları**altında **MFC kullanımını**bulun. Geçerli ayar kılavuzun sağ sütununda görünür. Geçerli ayara tıklayın ve **MFC 'Yi statik bir kitaplıkta kullanmak**üzere değiştirin.  
  
   4. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde **C/C++** klasörünü açın ve **Önişlemci**' yi seçin. Özellikler kılavuzunda **Önişlemci tanımlarını** bulun ve "ndebug" öğesini "_DEBUG" ile değiştirin.  
  
   5. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde, **bağlayıcı** klasörünü açın ve **giriş** kategorisini seçin. Özellikler kılavuzunda **ek bağımlılıklar**bulun. **Ek bağımlılıklar** ayarında "NAFXCWD" yazın. LIB "ve" LIBCMT. "  
  
   6. Yeni derleme seçeneklerini kaydetmek ve **Özellik sayfaları** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
5. **Derle** menüsünde **yeniden oluştur**' u seçin. Bu, tüm hata ayıklama bilgilerini modüllerinizle kaldırır ancak MFC kitaplığını etkilemez.  
  
6. Artık uygulamanızdaki seçili modüllere hata ayıklama bilgilerini geri eklemeniz gerekir. Kesme noktaları ayarlayabildiğinize ve yalnızca hata ayıklama bilgileriyle derlediğiniz modüllerde diğer hata ayıklayıcı işlevleri gerçekleştirebildiğinize unutmayın. Hata ayıklama bilgilerini dahil etmek istediğiniz her proje dosyası için aşağıdaki adımları uygulayın:  
  
   1. Çözüm Gezgini, projenizin altında bulunan **kaynak dosyaları** klasörünü açın.  
  
   2. Hata ayıklama bilgilerini ayarlamak istediğiniz dosyayı seçin.  
  
   3. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.  
  
   4. **Özellik sayfaları** Iletişim kutusundaki **yapılandırma ayarları** klasörü altında **C/C++** klasörünü açın ve **genel** kategorisini seçin.  
  
   5. Özellikler kılavuzunda **hata ayıklama bilgileri biçimini bulun.**  
  
   6. Hata ayıklama **bilgileri biçim** ayarlarına tıklayın ve hata ayıklama bilgileri için istediğiniz seçeneği (genellikle **/Zi**) seçin.  
  
   7. Uygulama Sihirbazı tarafından oluşturulan bir uygulama kullanıyorsanız veya önceden derlenmiş üstbilgilere sahipseniz, önceden derlenmiş üstbilgileri kapatmanız veya diğer modülleri derlerken önce yeniden derlemeniz gerekir. Aksi takdirde, uyarı C4650 ve hata iletisi C2855 alırsınız. ** \<Project> Özellikler** Iletişim kutusundaki **önceden derlenmiş üst bilgileri oluştur/kullan** ayarını değiştirerek (**yapılandırma özellikleri** klasörü, **C/C++** alt klasörü, **önceden derlenmiş üstbilgiler** kategorisi), önceden derlenmiş üst bilgileri devre dışı bırakabilirsiniz.  
  
7. **Oluşturma** menüsünde, güncel olmayan proje dosyalarını yeniden derlemek için **Oluştur** ' u seçin.  
  
   Bu konu başlığı altında açıklanan tekniğe alternatif olarak, her bir dosya için ayrı ayrı seçenekler tanımlamak üzere bir dış derleme görevleri dosyası kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarıyla bağlantı sağlamak için her modülün [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) bayrağını tanımlamanız gerekir. MFC sürüm kitaplıklarını kullanmak istiyorsanız, NDEBUG tanımlamanız gerekir. Dış makefiles yazma hakkında daha fazla bilgi için bkz. [NMAKE Başvurusu](https://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [Bu konuda](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama Visual C++](../debugger/debugging-native-code.md)
