---
title: MFC Hata Ayıklama Teknikleri | Microsoft Docs
description: Kodlu kesme noktaları, izleme, bellek sızıntısı algılama, nesne bellek dökümleri ve program boyutu azaltma gibi MFC programlarında hata ayıklama tekniklerini öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 458ffde8a2289608f1de0cd88689c4c718d4e300
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090648"
---
# <a name="mfc-debugging-techniques"></a>MFC Hata Ayıklama Teknikleri
Bir MFC programında hata ayıklarken bu hata ayıklama teknikleri yararlı olabilir.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konu başlığında
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[TRACE makrosu](#BKMK_The_TRACE_macro)

[MFC'de bellek sızıntılarını algılama](#BKMK_Memory_leak_detection_in_MFC)

- [Bellek ayırmalarını izleme](#BKMK_Tracking_memory_allocations)

- [Bellek tanılamayı etkinleştirme](#BKMK_Enabling_memory_diagnostics)

- [Bellek anlık görüntüleri alma](#BKMK_Taking_memory_snapshots)

- [Bellek istatistiklerini görüntüleme](#BKMK_Viewing_memory_statistics)

- [Nesne dökümlerini alma](#BKMK_Taking_object_dumps)

  - [Bellek dökümlerini yorumlama](#BKMK_Interpreting_memory_dumps)

  - [Nesne dökümlerini özelleştirme](#BKMK_Customizing_object_dumps)

  - [MFC Hata Ayıklama derlemesi boyutunu azaltma](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Seçili modüller için hata ayıklama bilgileriyle bir MFC uygulaması bina](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC, kaynak kodda sabit kodlama kesme noktaları için özel bir [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) işlevi sağlar:

```cpp
AfxDebugBreak( );
```

Intel `AfxDebugBreak` platformlarında, çekirdek kodu yerine kaynak kodunda hataya neden olan aşağıdaki kodu üretir:

```cpp
_asm int 3
```

Diğer platformlarda yalnızca `AfxDebugBreak` olarak çağrılır. `DebugBreak`

Bir yayın derlemesi `AfxDebugBreak` oluşturduktan veya bunları çevrelerken kullanmak için deyimlerini `#ifdef _DEBUG` kaldırarak emin olun.

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> TRACE makrosu
Programdan gelen iletileri hata ayıklayıcısı Çıkış penceresinde görüntülemek için [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) makrosu veya MFC [TRACE makrosu kullanabilirsiniz.](/previous-versions/6w95a4ha(v=vs.140)) [](../ide/reference/output-window.md) Onaylar [gibi](../debugger/c-cpp-assertions.md)izleme makroları da yalnızca program hata ayıklama sürümünde etkindir ve Yayın sürümünde derlenmiş olduğunda kaybolur.

Aşağıdaki örneklerde TRACE makrosu kullanma yollarından bazıları **verilmiştir.** gibi `printf` TRACE **makrosu** da bir dizi bağımsız değişkeni işebilir.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

TRACE makrosu hem karakter hem de veri \* wchar_t \* işler. Aşağıdaki örneklerde, FARKLı dize parametresi türleriyle birlikte TRACE makrosu kullanımı gösterildi.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

TRACE makrosu hakkında daha **fazla bilgi** için bkz. [Tanılama Hizmetleri.](/cpp/mfc/reference/diagnostic-services)

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> MFC'de bellek sızıntılarını algılama
MFC, ayrılan ancak hiçbir zaman taşınmamış belleği algılamak için sınıflar ve işlevler sağlar.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Bellek ayırmalarını izleme
MFC'de, bellek [sızıntılarını DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) için yeni  işleci yerine makroyu kullanabilirsiniz. Program hata ayıklama sürümünde, ayıran her bir nesne için dosya `DEBUG_NEW` adını ve satır numarasını takip eder. Programınıza ilişkin bir Yayın sürümünü derlerken, dosya adı ve satır `DEBUG_NEW` **numarası** bilgileri olmadan basit bir yeni işlemle çözümlenmiş olur. Bu nedenle, program yayın sürümünde hız cezası ödemezsiniz.

Yeni yerine kullanmak üzere tüm programınızı yeniden yazmak `DEBUG_NEW` istemiyorsanız, kaynak dosyalarınıza şu makroyu tanımlayabilirsiniz:

```cpp
#define new DEBUG_NEW
```

Bir nesne dökümü [ederek](#BKMK_Taking_object_dumps)ile ayrılan her nesne, ayrılan dosya ve satır numarasını gösterir, böylece bellek sızıntılarının `DEBUG_NEW` kaynaklarını tespit edersiniz.

MFC çerçevesinin Hata Ayıklama sürümü otomatik olarak `DEBUG_NEW` kullanır, ancak kodunuz bunu kullanmaz. 'nin avantajlarını elde etmek `DEBUG_NEW` için yukarıda gösterildiği gibi açıkça #define veya yeni bir `DEBUG_NEW` **uygulama** kullansanız gerekir.

[Bu konu başlığında](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Bellek tanılamayı etkinleştirme
Bellek tanılama olanaklarını kullanamadan önce tanılama izlemeyi etkinleştirmeniz gerekir.

**Bellek tanılamayı etkinleştirmek veya devre dışı bırakmak için**

- Tanılama belleği paylayıcısını etkinleştirmek veya devre dışı bırakmak için [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) genel işlevini çağırma. Bellek tanılaması hata ayıklama kitaplığında varsayılan olarak açıktır, bu işlevi genellikle bunları geçici olarak kapatmak için kullanır ve bu da program yürütme hızını artırır ve tanılama çıkışını azaltır.

  **afxMemDF ile belirli bellek tanılama özelliklerini seçmek için**

- Bellek tanılama özellikleri üzerinde daha kesin denetime sahip olmak için, MFC genel değişkeni [afxMemDF](/previous-versions/ahe4a83t(v=vs.140))değerini ayarerek tek tek bellek tanılama özelliklerini seçmeli olarak açabilirsiniz ve kapatabilirsiniz. Bu değişken, **numaralandı afxMemDF** türü tarafından belirtilen aşağıdaki değerlere sahip olabilir.

  |Değer|Açıklama|
  |-----------|-----------------|
  |**allocMemDF**|Tanılama belleği tanıyıyılayıcıyı (varsayılan) açma.|
  |**delayFreeMemDF**|Çağrılırken veya program `delete` çıkana kadar `free` belleğin serbest bırakılamasını geciktirin. Bu, programınız mümkün olan en fazla bellek miktarını ayırmaya neden olur.|
  |**checkAlwaysMemDF**|Bellek her ayrılırken veya serbest bırakılana [kadar AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) çağrısında bulundurabilirsiniz.|

  Bu değerler, burada gösterildiği gibi bir mantıksal OR işlemi gerçekleştirerek birlikte kullanılabilir:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Bu konu başlığında](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Bellek anlık görüntüleri alma

1. Bir [CMemoryState nesnesi](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) oluşturun ve [CMemoryState::Checkpoint üye işlevini](/cpp/mfc/reference/cmemorystate-structure#checkpoint) çağırabilirsiniz. Bu, ilk bellek anlık görüntüsünü oluşturur.

2. Programınız bellek ayırma ve ayırma işlemlerini gerçekleştirdikten sonra başka bir nesne `CMemoryState` oluşturun ve bu nesne için çağrısı `Checkpoint` gerçekleştirin. Bu, bellek kullanımının ikinci bir anlık görüntüsünü alır.

3. Üçüncü bir nesne `CMemoryState` oluşturun ve [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) üye işlevini çağırarak önceki iki nesneyi bağımsız değişken olarak `CMemoryState` sağlar. İki bellek durumları arasında bir fark varsa işlev sıfır `Difference` olmayan bir değer döndürür. Bu, bazı bellek bloklarının taşınmamış olduğunu gösterir.

    Bu örnek kodun nasıl göründüğünü gösterir:

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

    Bellek denetimi deyimlerinin, yalnızca program **#ifdef _DEBUG #endif** derlemek için bloklar / bloklar tarafından köşeli ayraç içine alınarak derlenmiş olduğunu fark edin.

    Artık bir bellek sızıntısı olduğunu annıza göre [CMemoryState::D umpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) gibi başka bir üye işlevi kullanabilirsiniz.

    [Bu konu başlığında](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Bellek istatistiklerini görüntüleme
[CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) işlevi, iki bellek durumu nesnesine bakarak yığından başlangıç ve bitiş durumları arasında atılmış nesneleri algılar. Bellek anlık görüntülerini aldıktan ve kullanarak karşılaştırdıktan sonra, çıkarılmamış nesneler hakkında bilgi almak için `CMemoryState::Difference` [CMemoryState::D umpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) çağırabilirsiniz.

Aşağıdaki örneği inceleyin:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Örnekten alınan örnek döküm şu şekildedir:

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

Serbest bloklar, olarak ayarlanırsa serbest bırakıla `afxMemDF` ertelenen `delayFreeMemDF` bloklardır.

İkinci satırda gösterilen sıradan nesne blokları yığında ayrılmış olarak kalır.

Nesne olmayan bloklar ile ayrılan dizileri ve yapıları `new` içerir. Bu durumda, yığında dört nesne olmayan blok ayrılmıştır ancak taşınmaz.

`Largest number used` , program tarafından herhangi bir zamanda kullanılan en yüksek belleği verir.

`Total allocations` program tarafından kullanılan toplam bellek miktarını verir.

[Bu konu başlığında](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Nesne dökümlerini alma
MFC programında [CMemoryState::D umpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullanarak yığında boşaltılmış olan tüm nesnelerin açıklamasının dökümlerini atabilirsiniz. `DumpAllObjectsSince` son [CMemoryState::Checkpoint'ten](/cpp/mfc/reference/cmemorystate-structure#checkpoint)sonra ayrılan tüm nesnelerin dökümlerini verir. Hiçbir `Checkpoint` çağrı alınmazsa, şu `DumpAllObjectsSince` anda bellekte olan tüm nesnelerin ve nesne olmayanların dökümlerini alır.

> [!NOTE]
> MFC nesne dökümlerini kullanamadan önce tanılama izlemeyi [etkinleştirmeniz gerekir.](#BKMK_Enabling_memory_diagnostics)

> [!NOTE]
> MFC, programınız çıkışta sızdırılan tüm nesnelerin dökümlerini otomatik olarak verir, bu nedenle bu noktada nesnelerin dökümlerini oluşturmak için kod oluşturmanıza gerek olmaz.

Aşağıdaki kod, iki bellek durumları karşılaştırarak bir bellek sızıntısını test eder ve bir sızıntı algılanırsa tüm nesnelerin dökümlerini verir.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

Döküm içeriği şu şekildedir:

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

Çoğu satırın başındaki küme ayraçları içinde bulunan sayılar, nesnelerin hangi sırayla ayrılmış olduğunu belirtir. En son ayrılan nesne en yüksek sayıya sahip ve dökümde en üstte görünür.

Bir nesne dökümünden maksimum bilgi miktarını almak için, nesne dökümlerini özelleştirmek için türetilmiş herhangi bir nesnenin üye `Dump` `CObject` işlevini geçersiz kılabilirsiniz.

Genel değişkeni küme ayraçlarında gösterilen sayıya ayarerek belirli bir bellek `_afxBreakAlloc` ayırmada kesme noktası ayarlayın. Programı yeniden çalıştırmanız, ayırma gerçekleştikleri zaman hata ayıklayıcının yürütmeyi kesmesi. Ardından çağrı yığınına bakarak program'nizin bu noktaya nasıl var olduğunu görmek için bu noktaya bakabilirsiniz.

C çalışma zamanı kitaplığı, C çalışma zamanı [ayırmaları _CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)gibi benzer bir işleve sahiptir.

[Bu konu başlığında](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Bellek dökümlerini yorumlama
Bu nesne dökümüne daha ayrıntılı bir şekilde bakın:

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

Bu dökümü oluşturan program yalnızca iki açık ayırmaya (biri yığında ve biri yığında) sahipti:

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

Oluşturucu, `CPerson` üye değişkenlerini başlatmak için kullanılan `char` işaretçiler olan üç bağımsız değişken `CString` alır. Bellek dökümünde nesnesini üç nesne olmayan `CPerson` blokla (3, 4 ve 5) birlikte görüntüebilirsiniz. Bunlar üye değişkenleri için `CString` karakterleri tutar ve nesne `CPerson` yıkıcısı çağrıldığında silinmez.

2 numaralı blok, nesnenin `CPerson` kendisidir. `$51A4` bloğun adresini temsil eder ve `CPerson` `Dump` ardından [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)tarafından çağrıldımızda :: tarafından çıkış olarak verilen nesnesinin içeriği takip eder.

1 numaralı blok sayısının, kare değişkendeki karakter sayısıyla eşleşen dizi numarası ve boyutu nedeniyle kare değişkeniyle ilişkili `CString` olduğunu tahmin `CString` edersiniz. Çerçevede ayrılan değişkenler, çerçeve kapsam dışında olduğunda otomatik olarak ayrılır.

**Çerçeve Değişkenleri**

Genel olarak, çerçeve değişkenleri kapsam dışında olduğunda otomatik olarak çıkarıldıklarından, çerçeve değişkenleriyle ilişkili yığın nesneleri konusunda endişelenmeyin. Bellek tanılama dökümleri içinde dağınıklığı önlemek için çağrılarınızı çerçeve değişkenlerinin kapsamının dışında `Checkpoint` olacak şekilde konumlandırmanız gerekir. Örneğin, burada gösterildiği gibi kapsam köşeli ayraçlarını önceki ayırma kodunun etrafına yerleştirin:

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

Kapsam köşeli ayraçları sağlanıyorsa, bu örneğin bellek dökümü aşağıdaki gibidir:

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

**Nesne Olmayan Ayırmalar**

Bazı ayırmaların nesneler (örneğin) ve bazılarının ise `CPerson` nesne olmayan ayırmalar olduğunu fark edersiniz. "Nesne olmayan ayırmalar", türetilmeyen nesnelere veya , veya gibi ilkel `CObject` C türlerinin `char` `int` ayırmalarıdır. `long` <strong>CObject türetilmiş sınıfı</strong>iç arabellekler için gibi ek alan ayırırsa, bu nesneler hem nesne hem de nesne olmayan ayırmaları gösterir.

**Bellek Sızıntılarını Önleme**

Yukarıdaki kodda, kare değişkeniyle ilişkili bellek bloğu otomatik olarak ve bellek sızıntısı olarak gösternmmektedir. `CString` Çerçeve değişkenleriyle ilişkili bellek sızıntılarının çoğunun, scoping kurallarıyla ilişkili otomatik ayırma ile ilgilenmesi.

Ancak yığında ayrılan nesneler için, bellek sızıntısını önlemek için nesneyi açıkça silmeniz gerekir. Önceki örnekteki son bellek sızıntısını temizlemek için yığında `CPerson` ayrılan nesneyi aşağıdaki gibi silin:

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[Bu konu başlığında](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Nesne dökümlerini özelleştirme
[CObject'den](/cpp/mfc/reference/cobject-class)bir sınıf türetseniz, Nesneleri Çıktı penceresine döküm almak için `Dump` [DumpAllObjectsSince'i](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullanarak ek bilgi sağlamak üzere üye işlevini [geçersiz kılabilirsiniz.](../ide/reference/output-window.md)

işlevi, nesnenin üye değişkenlerinin metinsel gösterimini döküm bağlamına `Dump` ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)) yazar. Döküm bağlamı, bir I/O akışına benzer. Bir veri göndermek için ekleme **<<** işlecini ( ) `CDumpContext` kullanabilirsiniz.

İşlevi geçersiz kılarak, temel sınıf nesnesinin içeriğini döküm etmek için ilk olarak temel `Dump` `Dump` sınıf sürümünü çağırabilirsiniz. Ardından, türetilmiş sınıfınıza ilişkin her üye değişkeni için metinsel bir açıklama ve değer çıktısı verir.

İşlevin bildirimi `Dump` şu şekildedir:

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

Nesne dökümlerinin dökümü yalnızca programda hata ayıklarken mantıklı olduğundan, işlevin bildirimi bir #ifdef _DEBUG / #endif `Dump` olur. 

Aşağıdaki örnekte işlev ilk `Dump` olarak temel sınıfı için işlevini `Dump` çağıran bir işlevdir. Ardından her üye değişkeninin kısa bir açıklamasını ve üyenin değerini tanılama akışına yazar.

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

Döküm çıkışını `CDumpContext` nereye gidereceklerini belirtmek için bir bağımsız değişken belirtmeniz gerekir. MFC'nin Hata Ayıklama sürümü, hata ayıklayıcıya çıkış `CDumpContext` gönderen adlı önceden tanımlanmış bir nesne `afxDump` sağlar.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> MFC Hata Ayıklama derlemesi boyutunu azaltma
Büyük bir MFC uygulamasının hata ayıklama bilgileri çok fazla disk alanı olabilir. Boyutu azaltmak için şu yordamlardan birini kullanabilirsiniz:

1. [/Z7, /Zi, /ZI (Hata](/cpp/build/reference/z7-zi-zi-debug-information-format) Ayıklama Bilgileri Biçimi) seçeneğini kullanarak ,Z7 yerine MFC **kitaplıklarını yeniden oluşturma.** Bu seçenekler, kitaplığın tamamına yönelik hata ayıklama bilgilerini içeren tek bir program veritabanı (PDB) dosyası oluşturur, bu da yedekliliği azaltır ve alan tasarrufu sağlar.

2. Hata ayıklama bilgileri olmadan MFC kitaplıklarını yeniden oluşturma [(/Z7, /Zi, /ZI (Hata Ayıklama Bilgileri Biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format) seçeneği yoktur). Bu durumda, hata ayıklama bilgileri olmaması, MFC kitaplık kodu içinde çoğu hata ayıklayıcı tesisini kullanmamanizi sağlar, ancak MFC kitaplıkları zaten kapsamlı olarak hata ayıklandı olduğundan, bu bir sorun olabilir.

3. Yalnızca aşağıda açıklandığı gibi seçilen modüller için hata ayıklama bilgileriyle kendi uygulamalarınızı derleme.

    [Bu konu başlığında](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Seçili modüller için hata ayıklama bilgileriyle bir MFC uygulaması bina
MFC hata ayıklama kitaplıkları ile seçilen modüllerin inşası, bu modüllerde adımlama ve diğer hata ayıklama olanaklarını kullanma imkanı sağlar. Bu yordam, projenin hem Hata Ayıklama hem de Yayın yapılandırmalarını kullanır, bu nedenle aşağıdaki adımlarda açıklanan değişiklikleri gerekli hale gelir (ve tam bir Yayın derlemesi gerektiğinde bir "hepsini yeniden derleme" gerekli hale gelir).

1. Bu Çözüm Gezgini projesini seçin.

2. Görünüm **menüsünden** Özellik **Sayfaları'ı seçin.**

3. İlk olarak, yeni bir proje yapılandırması oluşturacak.

   1. Özellik **\<Project> Sayfaları iletişim** kutusunda, Yapılandırma Yöneticisi **tıklayın.**

   2. Yeni [Yapılandırma Yöneticisi iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100))projenizi kılavuzda bulun. Yapılandırma **sütununda** öğesini **\<New...>** seçin.

   3. Yeni [Yapılandırma Project kutusuna](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100))yeni yapılandırmanız için "Kısmi Hata Ayıklama" gibi **bir Project** yazın.

   4. Kopyalama listesi **Ayarlar Yayın'ı** **seçin.**

   5. Yeni **Yapılandırma** iletişim kutusunu **kapatmak için Project'a** tıklayın.

   6. Yapılandırma Yöneticisi **iletişim** kutusunu kapatın.

4. Şimdi projenin tamamı için seçenekleri ayarlayabilirsiniz.

   1. Özellik **Sayfaları iletişim** kutusundaki Yapılandırma Özellikleri **klasörünün altında** Genel **kategorisini** seçin.

   2. Proje ayarları kılavuzunda **Varsayılanlar'Project (gerekirse)** genişletin.

   3. Varsayılanlar **Project altında** **MFC'nin Kullanımını bulun.** Geçerli ayar kılavuzun sağ sütununda görünür. Geçerli ayara tıklayın ve bunu Statik Kitaplıkta **MFC Kullan olarak değiştirebilirsiniz.**

   4. Özellikler Sayfaları iletişim kutusunun sol **bölmesinde** **C/C++** klasörünü açın ve Önişlemci'yi **seçin.** Özellikler kılavuzunda Önişlemci **Tanımları'ı bulun** ve "NDEBUG" ifadesini "_DEBUG" ile değiştirin.

   5. Özellikler Sayfaları iletişim kutusunun **sol bölmesinde,** **Linker** klasörünü açın ve Giriş Kategorisi'ni seçin.  Özellikler kılavuzunda Ek **Bağımlılıklar'ı bulun.** Ek **Bağımlılıklar ayarına** "NAFXCWD. LIB" ve "LIBCMT."

   6. Yeni **derleme** seçeneklerini kaydetmek ve Özellik Sayfaları iletişim kutusunu kapatmak için **Tamam'a** tıklayın.

5. Derleme **menüsünden Yeniden** **Oluştur'a tıklayın.** Bu, modüllerinizin tüm hata ayıklama bilgilerini kaldırır, ancak MFC kitaplığını etkilemez.

6. Şimdi uygulamanıza seçilen modüllere hata ayıklama bilgilerini eklemeniz gerekir. Kesme noktaları ayarlayabilirsiniz ve diğer hata ayıklayıcı işlevlerini yalnızca hata ayıklama bilgileriyle derledik modüllerde gerçekleştirebilirsiniz. Hata ayıklama bilgilerini dahil etmek istediğiniz her proje dosyası için aşağıdaki adımları gerçekleştirin:

   1. Bu Çözüm Gezgini projenizin **altında bulunan** Kaynak Dosyalar klasörünü açın.

   2. Hata ayıklama bilgilerini ayarlamak istediğiniz dosyayı seçin.

   3. Görünüm **menüsünden** Özellik **Sayfaları'ı seçin.**

   4. Özellik **Sayfaları iletişim** kutusundaki Yapılandırma Ayarlar **altında** **C/C++** klasörünü açın ve Genel **kategorisini** seçin.

   5. Özellikler kılavuzunda Hata Ayıklama **Bilgileri Biçimi'ne tıklayın.**

   6. Hata Ayıklama **Bilgileri Biçimi ayarlarına** tıklayın ve hata ayıklama bilgileri için istediğiniz seçeneği (genellikle **/ZI)** seçin.

   7. Uygulama sihirbazı tarafından oluşturulan bir uygulama kullanıyorsanız veya önceden oluşturulmuş üst bilgileri kullanıyorsanız, diğer modülleri derlemeden önce önceden oluşturulmuş üst bilgileri kapatmanız veya bunları yeniden derlemelisiniz. Aksi takdirde, C4650 uyarısı ve C2855 hata iletisi alırsınız. Özellikler iletişim kutusundaki (Yapılandırma Özellikleri klasörü, **\<Project>**  **C/C++** alt klasörü, Önceden DerlemeLi Üst Bilgiler kategorisi) Önceden DerlemeLi Üst Bilgiler ayarını değiştirerek önceden derlemeli üst bilgileri **kapatabilirsiniz.** 

7. Derleme **menüsünden,** güncel **olan proje** dosyalarını yeniden oluşturmak için Oluştur'a tıklayın.

   Bu konuda açıklanan tekniğin alternatifi olarak, her dosya için ayrı seçenekler tanımlamak üzere bir dış makefile kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarına bağlantı için her modül için [_DEBUG](/cpp/c-runtime-library/debug) bayrağını tanımlamanız gerekir. MFC sürüm kitaplıklarını kullanmak için NDEBUG tanımlamanız gerekir. Dış makefile'lar yazma hakkında daha fazla bilgi için [bkz. NMAKE Başvurusu.](/cpp/build/running-nmake)

   [Bu konu başlığında](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)