---
title: MFC hata ayıklama teknikleri | Microsoft Docs
ms.date: 11/04/2016
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
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06b42dbf31a8b5f4cb66de047bc1e08a4f840353
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600236"
---
# <a name="mfc-debugging-techniques"></a>MFC Hata Ayıklama Teknikleri
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

  - [MFC hata ayıklama derlemesinin boyutunu azaltma](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Seçilen modüller için hata ayıklama bilgileriyle bir MFC uygulaması oluşturma](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC, kaynak kodundaki sabit kodlama kesme noktaları için özel bir [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) işlevi sağlar:

```cpp
AfxDebugBreak( );
```

Intel platformlarında, `AfxDebugBreak` çekirdek kodu yerine kaynak kodu kesen aşağıdaki kodu üretir:

```cpp
_asm int 3
```

Diğer platformlarda `AfxDebugBreak` yalnızca çağırır `DebugBreak` .

`AfxDebugBreak`Bir yayın derlemesi oluştururken veya çevrelemek için kullandığınızda deyimleri kaldırmayı unutmayın `#ifdef _DEBUG` .

[Bu konuda](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> TRACE makrosu
Hata ayıklayıcı [çıktı penceresinde](../ide/reference/output-window.md)programınızdaki iletileri göstermek Için, [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) makrosunu veya MFC [Trace](/previous-versions/6w95a4ha(v=vs.140)) makrosunu kullanabilirsiniz. [Onaylamalar](../debugger/c-cpp-assertions.md)gibi, izleme makroları yalnızca programınızın hata ayıklama sürümünde etkindir ve yayın sürümünde derlendiğinde kaybolur.

Aşağıdaki örneklerde, **izleme** makrosunu kullanabileceğiniz bazı yollar gösterilmektedir. Benzer şekilde `printf` , **Trace** makrosu bir dizi bağımsız değişkeni işleyebilir.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

TRACE makrosu hem char hem de wchar_t parametrelerini uygun şekilde işler \* \* . Aşağıdaki örneklerde, farklı dize parametresi türleriyle birlikte Izleme makrosunun kullanımı gösterilmektedir.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

**İzleme** makrosu hakkında daha fazla bilgi için bkz. [Tanılama Hizmetleri](/cpp/mfc/reference/diagnostic-services).

[Bu konuda](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> MFC 'de bellek sızıntılarını algılama
MFC, ayrılan ancak serbest bırakılmakta olan belleği algılamaya yönelik sınıfları ve işlevleri sağlar.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Bellek ayırmalarını izleme
MFC 'de, bellek sızıntılarını bulmaya yardımcı olması için **Yeni** işlecin yerine makro [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) kullanabilirsiniz. Programınızın hata ayıklama sürümünde, `DEBUG_NEW` ayırdığı her bir nesne için dosya adını ve satır numarasını izler. Programınızın bir yayın sürümünü derlerken `DEBUG_NEW` dosya adı ve satır numarası bilgisi olmadan basit bir **Yeni** işlem olarak çözümlenir. Bu nedenle, programınızın yayın sürümünde hiçbir hızda ceza puanı ödeyin.

Yeni bir yerde kullanmak üzere tüm programınızı yeniden yazmak istemiyorsanız `DEBUG_NEW` , bu makroyu kaynak dosyalarınızda **new**tanımlayabilirsiniz:

```cpp
#define new DEBUG_NEW
```

Bir [nesne dökümü](#BKMK_Taking_object_dumps)gerçekleştirdiğinizde, ile ayrılan her bir nesne, `DEBUG_NEW` ayrılan dosya ve satır numarasını gösterir ve bellek sızıntıları kaynaklarını bulmanızı sağlar.

MFC çerçevesinin hata ayıklama sürümü `DEBUG_NEW` otomatik olarak kullanır, ancak kodunuz değildir. Avantajlarından yararlanmak istiyorsanız `DEBUG_NEW` , `DEBUG_NEW` yukarıda gösterildiği gibi açıkça veya **#define yeni** kullanmanız gerekir.

[Bu konuda](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Bellek tanılamayı etkinleştirme
Bellek Tanılama tesislerini kullanabilmeniz için, tanılama izlemeyi etkinleştirmeniz gerekir.

**Bellek tanılamayı etkinleştirmek veya devre dışı bırakmak için**

- Tanılama bellek ayırıcısını etkinleştirmek veya devre dışı bırakmak için [Afxenablememoryıtracking](/previous-versions/hzsxb6e8(v=vs.140)) genel işlevini çağırın. Bellek Tanılama, hata ayıklama kitaplığı 'nda varsayılan olarak açık olduğundan, genellikle bu işlevi, program yürütme hızını artıran ve tanılama çıkışını azaltan, geçici olarak devre dışı bırakmak için kullanacaksınız.

  **AfxMemDF ile belirli bellek tanılama özelliklerini seçmek için**

- Bellek tanılama özellikleri üzerinde daha kesin bir denetim istiyorsanız, [afxMemDF](/previous-versions/ahe4a83t(v=vs.140))MFC genel değişkeninin değerini ayarlayarak, tek tek Bellek Tanılama özelliklerini seçmeli şekilde açıp kapatabilirsiniz. Bu değişken, sıralanmış tür **afxMemDF**tarafından belirtilen şekilde aşağıdaki değerlere sahip olabilir.

  |Değer|Açıklama|
  |-----------|-----------------|
  |**allocMemDF**|Tanılama belleği ayırıcısını açın (varsayılan).|
  |**delayFreeMemDF**|Çağırma sırasında `delete` veya `free` Program kapatılıncaya kadar bellek boşaltmayı geciktir. Bu, programınızın mümkün olan en yüksek miktarda belleği ayırmasına neden olur.|
  |**Checkalwaykokmdf**|Bellek ayrıldığı veya serbest bırakılmış her seferinde [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) çağrısı yapın.|

  Bu değerler, burada gösterildiği gibi mantıksal veya işlem gerçekleştirerek birlikte kullanılabilir:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Bu konuda](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Bellek anlık görüntülerini alma

1. Bir [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) nesnesi oluşturun ve [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) üye işlevini çağırın. Bu, ilk bellek anlık görüntüsünü oluşturur.

2. Programınız bellek ayırmayı ve ayırmayı kaldırma işlemlerini gerçekleştirdikten sonra, `CMemoryState` Bu nesne için başka bir nesne ve çağrı oluşturun `Checkpoint` . Bu, bellek kullanımının ikinci bir anlık görüntüsünü alır.

3. Üçüncü bir `CMemoryState` nesne oluşturun ve [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) üye işlevini çağırın ve bu iki önceki nesne bağımsız değişken olarak sağlama `CMemoryState` . İki bellek durumu arasında bir fark varsa, `Difference` işlev sıfır dışında bir değer döndürür. Bu, bazı bellek bloklarının serbest bırakılmadığını gösterir.

    Bu örnekte kodun nasıl göründüğü gösterilmektedir:

    ```cpp
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

    Bellek denetimi deyimlerinin, yalnızca programınızın hata ayıklama sürümlerinde derlenmesi için **#ifdef _debug/#endif** blokları tarafından parantez içine alınmış olduğuna dikkat edin.

    Artık bir bellek sızıntısı olduğunu öğrenmiş olduğunuza göre, diğer bir üye işlevi olan [CMemoryState::D Fertime istatistiklerini](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) bulmanıza yardımcı olacak şekilde kullanabilirsiniz.

    [Bu konuda](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Bellek istatistiklerini görüntüleme
[CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) işlevi iki bellek durumu nesnesine bakar ve başlangıç ve bitiş durumları arasında yığından serbest bırakılmayan nesneleri algılar. Bellek anlık görüntülerini aldıktan ve kullanarak bunları karşılaştırdıktan sonra `CMemoryState::Difference` , serbest bırakılmayan nesneler hakkında bilgi almak Için [CMemoryState::D öncelik istatistiklerini](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) çağırabilirsiniz.

Aşağıdaki örneği inceleyin:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Örnekteki örnek bir döküm şöyle görünür:

```cpp
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
Bir MFC programında, yığın üzerinde serbest bırakılmayan tüm nesnelerin bir açıklamasının dökümünü almak için [CMemoryState::D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullanabilirsiniz. `DumpAllObjectsSince` Son [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint)öğesinden bu yana ayrılan tüm nesneleri döker. Hiçbir `Checkpoint` çağrı gerçekleşmiyor ise, `DumpAllObjectsSince` tüm nesneleri ve şu anda bellekte olmayan nesneleri döker.

> [!NOTE]
> MFC nesne dökümünü kullanabilmeniz için, [Tanılama izlemeyi etkinleştirmeniz](#BKMK_Enabling_memory_diagnostics)gerekir.

> [!NOTE]
> MFC, programınız çıktığında tüm sızdırılan nesneleri otomatik olarak döker, bu nedenle bu noktada nesnelerin dökümünü yapmak için kod oluşturmanız gerekmez.

Aşağıdaki kod, iki bellek durumunu karşılaştırarak bir bellek sızıntısını sınar ve bir sızıntı algılanırsa tüm nesneleri döker.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

Döküm içeriği şöyle görünür:

```cmd
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

C çalışma zamanı kitaplığı, C çalışma zamanı ayırmaları için kullanabileceğiniz benzer bir işleve sahiptir [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc).

[Bu konuda](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Bellek dökümlerini yorumlama
Daha ayrıntılı bilgi için bu nesne dökümünden bakın:

```cmd
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

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

`CPerson`Oluşturucu, `char` üye değişkenlerini başlatmak için kullanılan işaretçiler olan üç bağımsız değişken alır `CString` . Bellek dökümünde, `CPerson` nesneyi üç nesne olmayan blok (3, 4 ve 5) ile birlikte görebilirsiniz. Bunlar `CString` üye değişkenlerinin karakterlerini tutar ve `CPerson` nesne yıkıcısı çağrıldığında silinmez.

Blok numarası 2 `CPerson` nesnenin kendisidir. `$51A4` bloğunun adresini temsil eder ve öğesinden sonra, `CPerson` `Dump` [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)tarafından çağrıldığında::.

`CString`Çerçeve değişkeninde karakter sayısıyla eşleşen sıra numarası ve boyutu nedeniyle, 1 blok numarası çerçeve değişkeniyle ilişkili olduğunu tahmin edebilirsiniz `CString` . Çerçeve kapsam dışına geçtiğinde çerçevede ayrılan değişkenler otomatik olarak serbest bırakılır.

**Çerçeve değişkenleri**

Genel olarak, çerçeve değişkenleri kapsam dışına dönerek serbest bırakıldıklarından, çerçeve değişkenleriyle ilişkili yığın nesneleri hakkında endişelenmemelisiniz. Bellek Tanılama dökümlerinizin dağınıklığını önlemek için, çağrılarınızı `Checkpoint` çerçeve değişkenlerinin kapsamı dışında olacak şekilde konumlandırmalısınız. Örneğin, aşağıda gösterildiği gibi, önceki ayırma kodunun etrafına kapsam ayraçları yerleştirin:

```cpp
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

```cmd
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

Bazı ayırmaların nesneler (gibi `CPerson` ) ve bazıları ise nesne olmayan ayırmalar olduğunu unutmayın. "Nesne olmayan ayırmalar",, veya gibi temel C türlerinden türetilmeyen nesneler için ayırmalar `CObject` `char` `int` `long` . <strong>CObject ile</strong>türetilmiş sınıf, iç arabellekler gibi ek alan ayırırsa, bu nesneler hem nesne hem de nesne olmayan ayırmaları gösterir.

**Bellek sızıntılarını önlemek**

Yukarıdaki kodda, çerçeve değişkeniyle ilişkili bellek bloğunun `CString` otomatik olarak serbest bırakılmış olduğunu ve bellek sızıntısı olarak gösterilmediğine dikkat edin. Kapsam kurallarıyla ilişkili otomatik ayırmayı kaldırma, çerçeve değişkenleriyle ilişkili çoğu bellek sızıntılarını üstlenir.

Ancak yığında ayrılan nesneler için, bir bellek sızıntısını engellemek için nesneyi açıkça silmeniz gerekir. Önceki örnekte yer alan son bellek sızıntısını temizlemek için, `CPerson` yığında ayrılan nesneyi aşağıdaki gibi silin:

```cpp
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
[CObject](/cpp/mfc/reference/cobject-class)'ten bir sınıf türettiğinizde, `Dump` nesneleri [Çıkış penceresinde](../ide/reference/output-window.md)dökmek için [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullandığınızda ek bilgi sağlamak için üye işlevini geçersiz kılabilirsiniz.

`Dump`İşlevi, bir döküm bağlamına ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)) nesnenin üye değişkenlerinin metinsel bir gösterimini yazar. Döküm bağlamı bir g/ç akışına benzer. ' **<<** A veri göndermek için ekleme işlecini () kullanabilirsiniz `CDumpContext` .

İşlevi geçersiz kıldığınızda `Dump` , `Dump` temel sınıf nesnesinin içeriğinin dökümünü yapmak için önce temel sınıf sürümünü çağırmanız gerekir. Ardından, türetilmiş sınıfınızın her bir üye değişkeni için bir metinsel açıklama ve değer çıkışı yapın.

İşlevin bildirimi şöyle `Dump` görünür:

```cpp
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

```cpp
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

```cpp
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

1. /Z7 yerine [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format) SEÇENEĞINI kullanarak MFC kitaplıklarını yeniden derleyin **.** Bu seçenekler, tüm kitaplık için hata ayıklama bilgilerini içeren tek bir program veritabanı (PDB) dosyası oluşturur, artıklığı azaltır ve alan tasarrufu yapın.

2. MFC kitaplıklarını hata ayıklama bilgileri olmadan yeniden derleyin ( [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format) seçeneği). Bu durumda, hata ayıklama bilgilerinin bulunmaması, MFC kitaplık kodu içindeki çoğu hata ayıklayıcı tesislerini kullanmanızı önler, ancak MFC kitaplıklarının zaten kapsamlı bir şekilde ayıklandığından bu sorun olmayabilir.

3. Aşağıda açıklandığı gibi, seçilen modüller için hata ayıklama bilgileri ile kendi uygulamanızı oluşturun.

    [Bu konuda](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Seçilen modüller için hata ayıklama bilgileriyle bir MFC uygulaması oluşturma
MFC hata ayıklama kitaplıklarıyla seçili modüllerin oluşturulması, bu modüllerde adımlamayı ve diğer hata ayıklama olanaklarını kullanmanıza olanak sağlar. Bu yordam, projenin hata ayıklama ve sürüm yapılandırmalarının yanı sıra, aşağıdaki adımlarda açıklanan değişiklikleri tasarımda (ve ayrıca tam bir yayın derlemesi gerektiğinde "tümünü yeniden derle" seçeneğini de yapar).

1. Çözüm Gezgini, projeyi seçin.

2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

3. İlk olarak yeni bir proje yapılandırması oluşturacaksınız.

   1. ** \<Project> Özellik sayfaları** iletişim kutusunda **Configuration Manager** düğmesine tıklayın.

   2. [Configuration Manager iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), kılavuzdaki projenizi bulun. **Yapılandırma** sütununda, öğesini seçin **\<New...>** .

   3. [Yeni proje yapılandırması iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), yeni yapılandırmanız Için, **Proje yapılandırma adı** kutusuna "kısmi hata ayıklama" gibi bir ad yazın.

   4. **Ayarları Şuradan Kopyala** listesinden **yayın**' ı seçin.

   5. **Yeni proje yapılandırması** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

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

   Bu konu başlığı altında açıklanan tekniğe alternatif olarak, her bir dosya için ayrı ayrı seçenekler tanımlamak üzere bir dış derleme görevleri dosyası kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarıyla bağlantı sağlamak için her modülün [_DEBUG](/cpp/c-runtime-library/debug) bayrağını tanımlamanız gerekir. MFC sürüm kitaplıklarını kullanmak istiyorsanız, NDEBUG tanımlamanız gerekir. Dış makefiles yazma hakkında daha fazla bilgi için bkz. [NMAKE Başvurusu](/cpp/build/running-nmake).

   [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)