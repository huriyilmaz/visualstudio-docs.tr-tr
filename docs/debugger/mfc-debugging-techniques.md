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
ms.openlocfilehash: da1da728ffb68d4701e4925809db669c84199696f08309a165fdbfc819a3d852
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239642"
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

Bir yayın `AfxDebugBreak` derlemesi oluşturduktan veya bunları çevrelerken kullanmak için deyimlerini `#ifdef _DEBUG` kaldırarak emin olun.

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
MFC'de, bellek [sızıntılarını DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) yardımcı olmak için yeni **işleci** yerine makroyu kullanabilirsiniz. Program hata ayıklama sürümünde, ayıran her bir nesne için dosya adını ve `DEBUG_NEW` satır numarasını takip eder. Programınıza ilişkin bir Yayın sürümünü derlerken, dosya adı ve satır numarası `DEBUG_NEW` bilgileri olmadan basit bir yeni işlemle çözümlenmiş olur.  Bu nedenle, program yayın sürümünde hız cezası ödemezsiniz.

Yeni yerine kullanmak üzere tüm programınızı yeniden yazmak `DEBUG_NEW` istemiyorsanız, kaynak dosyalarınıza şu makroyu tanımlayabilirsiniz:

```cpp
#define new DEBUG_NEW
```

Bir nesne dökümü [ederek](#BKMK_Taking_object_dumps)ile ayrılan her nesne, ayrılan dosya ve satır numarasını gösterir, böylece bellek sızıntılarının `DEBUG_NEW` kaynaklarını tespit edersiniz.

MFC çerçevesinin Hata Ayıklama sürümü otomatik olarak `DEBUG_NEW` kullanır, ancak kodunuz bunu kullanmaz. 'nin avantajlarını elde `DEBUG_NEW` etmek için yukarıda gösterildiği gibi açıkça #define veya yeni bir `DEBUG_NEW` **uygulama** kullansanız gerekir.

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
  |**checkAlwaysMemDF**|Bellek her serbest bırakıldı veya serbest bırakıldıkında [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) çağrısı.|

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

    Bellek denetimi deyimlerinin, yalnızca program **#ifdef _DEBUG #endif** derlemek için #ifdef _DEBUG / bloklar tarafından köşeli ayraç içine alınarak derlenmiş olduğunu fark edin.

    Artık bir bellek sızıntısı olduğunu annıza göre [CMemoryState::D umpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) gibi başka bir üye işlevi kullanabilirsiniz.

    [Bu konu başlığında](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Bellek istatistiklerini görüntüleme
[CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) işlevi, iki bellek durumu nesnesine bakarak yığından başlangıç ve bitiş durumları arasında bırakılmış nesneleri algılar. Bellek anlık görüntülerini aldıktan ve kullanarak karşılaştırdıktan sonra, çıkarılmamış nesneler hakkında bilgi almak için `CMemoryState::Difference` [CMemoryState::D umpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) çağırabilirsiniz.

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

Nesne olmayan bloklar ile ayrılan dizileri ve yapıları `new` içerir. Bu durumda, yığında dört nesne olmayan blok ayrılmıştır ancak atılmış değildir.

`Largest number used` , program tarafından herhangi bir zamanda kullanılan en yüksek belleği verir.

`Total allocations` program tarafından kullanılan toplam bellek miktarını verir.

[Bu konu başlığında](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Nesne dökümlerini alma
MFC programında [CMemoryState::D umpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullanarak, yığında boşaltılmış olan tüm nesnelerin açıklamasının dökümlerini atabilirsiniz. `DumpAllObjectsSince` son [CMemoryState::Checkpoint'ten](/cpp/mfc/reference/cmemorystate-structure#checkpoint)sonra ayrılan tüm nesnelerin dökümlerini verir. Hiçbir `Checkpoint` çağrı alınmazsa, şu `DumpAllObjectsSince` anda bellekte olan tüm nesnelerin ve nesne olmayanların dökümlerini alır.

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

Genel değişkeni küme ayraçlarında gösterilen sayıya ayarerek belirli bir bellek `_afxBreakAlloc` ayırmada kesme noktası ayarlayın. Programı yeniden çalıştırmanız, ayırma sırasında hata ayıklayıcının yürütmeyi durdurmasını sağlar. Ardından, programınızın bu noktaya nasıl kullanıldığını görmek için çağrı yığınına bakabilirsiniz.

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

   1. **\<Project> Özellik sayfaları** iletişim kutusunda **Configuration Manager** düğmesine tıklayın.

   2. [Configuration Manager iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), kılavuzdaki projenizi bulun. **Yapılandırma** sütununda, öğesini seçin **\<New...>** .

   3. [yeni Project yapılandırması iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), yeni yapılandırmanız için, **Project yapılandırma adı** kutusuna "kısmi hata ayıklama" gibi bir ad yazın.

   4. **kopyalama Ayarlar** listeden **yayınla**' yı seçin.

   5. **yeni Project yapılandırma** iletişim kutusunu kapatmak için **tamam** ' ı tıklatın.

   6. **Configuration Manager** iletişim kutusunu kapatın.

4. Şimdi tüm projenin seçeneklerini ayarlayacaksınız.

   1. **Özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörü altında **genel** kategorisini seçin.

   2. proje ayarları kılavuzunda **Project varsayılanlar** ' ı genişletin (gerekirse).

   3. **Project varsayılanları** altında **MFC kullanımını** bulun. Geçerli ayar kılavuzun sağ sütununda görünür. Geçerli ayara tıklayın ve **MFC 'Yi statik bir kitaplıkta kullanmak** üzere değiştirin.

   4. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde **C/C++** klasörünü açın ve **Önişlemci**' yi seçin. Özellikler kılavuzunda **Önişlemci tanımlarını** bulun ve "ndebug" öğesini "_DEBUG" ile değiştirin.

   5. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde, **bağlayıcı** klasörünü açın ve **giriş** kategorisini seçin. Özellikler kılavuzunda **ek bağımlılıklar** bulun. **Ek bağımlılıklar** ayarında "NAFXCWD" yazın. LIB "ve" LIBCMT. "

   6. Yeni derleme seçeneklerini kaydetmek ve **Özellik sayfaları** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. **Derle** menüsünde **yeniden oluştur**' u seçin. Bu, tüm hata ayıklama bilgilerini modüllerinizle kaldırır ancak MFC kitaplığını etkilemez.

6. Artık uygulamanızdaki seçili modüllere hata ayıklama bilgilerini geri eklemeniz gerekir. Kesme noktaları ayarlayabildiğinize ve yalnızca hata ayıklama bilgileriyle derlediğiniz modüllerde diğer hata ayıklayıcı işlevleri gerçekleştirebildiğinize unutmayın. Hata ayıklama bilgilerini dahil etmek istediğiniz her proje dosyası için aşağıdaki adımları uygulayın:

   1. Çözüm Gezgini, projenizin altında bulunan **kaynak dosyaları** klasörünü açın.

   2. Hata ayıklama bilgilerini ayarlamak istediğiniz dosyayı seçin.

   3. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

   4. **özellik sayfaları** iletişim kutusundaki **yapılandırma Ayarlar** klasörü altında, **C/C++** klasörünü açın ve **genel** kategorisini seçin.

   5. Özellikler kılavuzunda **hata ayıklama bilgileri biçimini bulun.**

   6. Hata ayıklama **bilgileri biçim** ayarlarına tıklayın ve hata ayıklama bilgileri için istediğiniz seçeneği (genellikle **/Zi**) seçin.

   7. Uygulama Sihirbazı tarafından oluşturulan bir uygulama kullanıyorsanız veya önceden derlenmiş üstbilgilere sahipseniz, önceden derlenmiş üstbilgileri kapatmanız veya diğer modülleri derlerken önce yeniden derlemeniz gerekir. Aksi takdirde, uyarı C4650 ve hata iletisi C2855 alırsınız. **\<Project> Özellikler** Iletişim kutusundaki **önceden derlenmiş üst bilgileri oluştur/kullan** ayarını değiştirerek (**yapılandırma özellikleri** klasörü, **C/C++** alt klasörü, **önceden derlenmiş üstbilgiler** kategorisi), önceden derlenmiş üst bilgileri devre dışı bırakabilirsiniz.

7. **Oluşturma** menüsünde, güncel olmayan proje dosyalarını yeniden derlemek için **Oluştur** ' u seçin.

   Bu konu başlığı altında açıklanan tekniğe alternatif olarak, her bir dosya için ayrı ayrı seçenekler tanımlamak üzere bir dış derleme görevleri dosyası kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarıyla bağlantı sağlamak için her modülün [_DEBUG](/cpp/c-runtime-library/debug) bayrağını tanımlamanız gerekir. MFC sürüm kitaplıklarını kullanmak istiyorsanız, NDEBUG tanımlamanız gerekir. Dış makefiles yazma hakkında daha fazla bilgi için bkz. [NMAKE Başvurusu](/cpp/build/running-nmake).

   [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)