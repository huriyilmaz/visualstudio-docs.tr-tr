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
ms.openlocfilehash: 1380cf2cfd4d1ffe729fdd4a6ce9cfb2ba7d9ab6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435652"
---
# <a name="mfc-debugging-techniques"></a>MFC Hata Ayıklama Teknikleri
MFC programında hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.

## <a name="BKMK_In_this_topic"></a>Bu konuda
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

## <a name="BKMK_AfxDebugBreak"></a>AfxDebugBreak
MFC, kaynak kodundaki sabit kodlama kesme noktaları için özel bir [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) işlevi sağlar:

```cpp
AfxDebugBreak( );
```

Intel platformlarında `AfxDebugBreak`, çekirdek kodu yerine kaynak kodu kesen aşağıdaki kodu üretir:

```cpp
_asm int 3
```

Diğer platformlarda `AfxDebugBreak` yalnızca `DebugBreak` ' i çağırır.

Yayın derlemesi oluştururken `AfxDebugBreak` deyimlerini kaldırdığınızdan emin olun veya onları çevrelemek için `#ifdef _DEBUG` kullanın.

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_The_TRACE_macro"></a>TRACE makrosu
Hata ayıklayıcı [çıktı penceresinde](../ide/reference/output-window.md)programınızdaki iletileri göstermek Için, [ATLTRACE](https://msdn.microsoft.com/Library/c796baa5-e2b9-4814-a27d-d800590b102e) makrosunu veya MFC [Trace](https://msdn.microsoft.com/Library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) makrosunu kullanabilirsiniz. [Onaylamalar](../debugger/c-cpp-assertions.md)gibi, izleme makroları yalnızca programınızın hata ayıklama sürümünde etkindir ve yayın sürümünde derlendiğinde kaybolur.

Aşağıdaki örneklerde, **izleme** makrosunu kullanabileceğiniz bazı yollar gösterilmektedir. @No__t-0 gibi, **izleme** makrosu bir dizi bağımsız değişkeni işleyebilir.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

TRACE makrosu hem char @ no__t-0 hem de wchar_t @ no__t-1 parametrelerini uygun şekilde işler. Aşağıdaki örneklerde, farklı dize parametresi türleriyle birlikte Izleme makrosunun kullanımı gösterilmektedir.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

**İzleme** makrosu hakkında daha fazla bilgi için bkz. [Tanılama Hizmetleri](/cpp/mfc/reference/diagnostic-services).

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Memory_leak_detection_in_MFC"></a>MFC 'de bellek sızıntılarını algılama
MFC, ayrılan ancak serbest bırakılmakta olan belleği algılamaya yönelik sınıfları ve işlevleri sağlar.

### <a name="BKMK_Tracking_memory_allocations"></a>Bellek ayırmalarını izleme
MFC 'de, bellek sızıntılarını bulmaya yardımcı olması için **Yeni** Işlecin yerine [DEBUG_NEW](https://msdn.microsoft.com/Library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) makrosunu kullanabilirsiniz. Programınızın hata ayıklama sürümünde, `DEBUG_NEW`, ayırdığı her nesne için dosya adını ve satır numarasını izler. Programınızın bir yayın sürümünü derlerken, `DEBUG_NEW` dosya adı ve satır numarası bilgisi olmadan basit bir **Yeni** işlem olarak çözümlenir. Bu nedenle, programınızın yayın sürümünde hiçbir hızda ceza puanı ödeyin.

**Yeni**bir yerinde `DEBUG_NEW` kullanmak üzere tüm programınızı yeniden yazmak istemiyorsanız, bu makroyu kaynak dosyalarınızda tanımlayabilirsiniz:

```cpp
#define new DEBUG_NEW
```

Bir [nesne dökümü](#BKMK_Taking_object_dumps)gerçekleştirdiğinizde, `DEBUG_NEW` ile ayrılan her nesne, ayrılan dosya ve satır numarasını gösterir ve bellek sızıntıları kaynaklarını bulmanızı sağlar.

MFC çerçevesinin hata ayıklama sürümü otomatik olarak `DEBUG_NEW` kullanır, ancak kodunuz değildir. @No__t avantajlarından yararlanmak istiyorsanız, yukarıda gösterildiği gibi `DEBUG_NEW` ' i açıkça veya **#define yeni** kullanmanız gerekir.

[Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Enabling_memory_diagnostics"></a>Bellek tanılamayı etkinleştirme
Bellek Tanılama tesislerini kullanabilmeniz için, tanılama izlemeyi etkinleştirmeniz gerekir.

**Bellek tanılamayı etkinleştirmek veya devre dışı bırakmak için**

- Tanılama bellek ayırıcısını etkinleştirmek veya devre dışı bırakmak için [Afxenablememoryıtracking](https://msdn.microsoft.com/Library/0a40e0c4-855d-46e2-9577-a8f2346f47db) genel işlevini çağırın. Bellek Tanılama, hata ayıklama kitaplığı 'nda varsayılan olarak açık olduğundan, genellikle bu işlevi, program yürütme hızını artıran ve tanılama çıkışını azaltan, geçici olarak devre dışı bırakmak için kullanacaksınız.

  **AfxMemDF ile belirli bellek tanılama özelliklerini seçmek için**

- Bellek tanılama özellikleri üzerinde daha kesin bir denetim istiyorsanız, [afxMemDF](https://msdn.microsoft.com/Library/cf117501-5446-4fce-81b3-f7194bc95086)MFC genel değişkeninin değerini ayarlayarak, tek tek Bellek Tanılama özelliklerini seçmeli şekilde açıp kapatabilirsiniz. Bu değişken, sıralanmış tür **afxMemDF**tarafından belirtilen şekilde aşağıdaki değerlere sahip olabilir.

  |Değer|Açıklama|
  |-----------|-----------------|
  |**allocMemDF**|Tanılama belleği ayırıcısını açın (varsayılan).|
  |**delayFreeMemDF**|Program kapatılıncaya kadar `delete` veya `free` çağrılırken belleği boşaltmayı geciktir. Bu, programınızın mümkün olan en yüksek miktarda belleği ayırmasına neden olur.|
  |**Checkalwaykokmdf**|Bellek ayrıldığı veya serbest bırakılmış her seferinde [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) çağrısı yapın.|

  Bu değerler, burada gösterildiği gibi mantıksal veya işlem gerçekleştirerek birlikte kullanılabilir:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Taking_memory_snapshots"></a>Bellek anlık görüntülerini alma

1. Bir [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) nesnesi oluşturun ve [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) üye işlevini çağırın. Bu, ilk bellek anlık görüntüsünü oluşturur.

2. Programınız bellek ayırmayı ve ayırmayı kaldırma işlemlerini gerçekleştirdikten sonra, başka bir `CMemoryState` nesnesi oluşturun ve bu nesne için `Checkpoint` ' i çağırın. Bu, bellek kullanımının ikinci bir anlık görüntüsünü alır.

3. Üçüncü bir `CMemoryState` nesnesi oluşturun ve [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) üye işlevini çağırın ve bu iki önceki `CMemoryState` nesnesine bağımsız değişken olarak sağlama. İki bellek durumu arasında bir fark varsa `Difference` işlevi sıfır dışında bir değer döndürür. Bu, bazı bellek bloklarının serbest bırakılmadığını gösterir.

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

    Bellek denetleme deyimlerinin yalnızca programınızın hata ayıklama sürümlerinde derlenmesi için **#ifdef _debug/#endif** blokları tarafından parantez içine alınmış olduğuna dikkat edin.

    Artık bir bellek sızıntısı olduğunu öğrenmiş olduğunuza göre, diğer bir üye işlevi olan [CMemoryState::D Fertime istatistiklerini](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) bulmanıza yardımcı olacak şekilde kullanabilirsiniz.

    [Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Viewing_memory_statistics"></a>Bellek istatistiklerini görüntüleme
[CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) işlevi iki bellek durumu nesnesine bakar ve başlangıç ve bitiş durumları arasında yığından serbest bırakılmayan nesneleri algılar. Bellek anlık görüntülerini aldıktan ve `CMemoryState::Difference` ' ı kullanarak karşılaştırdıktan sonra, serbest bırakılmayan nesneler hakkında bilgi almak için [CMemoryState::D öncelik istatistiklerini](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) çağırabilirsiniz.

Aşağıdaki örneği göz önünde bulundurun:

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

Boş bloklar `afxMemDF` `delayFreeMemDF` olarak ayarlandıysa, ayırmayı kaldırma geciktirilen bloklardır.

İkinci satırda gösterilen sıradan nesne blokları, yığında ayrılmaya devam eder.

Nesne olmayan bloklar `new` ile ayrılmış dizileri ve yapıları içerir. Bu durumda, yığında dört nesne olmayan blok ayrılmıştı ancak serbest bırakılmamalıdır.

`Largest number used`, program tarafından herhangi bir zamanda kullanılan en fazla bellek sayısını verir.

`Total allocations`, program tarafından kullanılan toplam bellek miktarını verir.

[Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Taking_object_dumps"></a>Nesne dökümlerini alma
Bir MFC programında, yığın üzerinde serbest bırakılmayan tüm nesnelerin bir açıklamasının dökümünü almak için [CMemoryState::D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullanabilirsiniz. `DumpAllObjectsSince`, son [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint)öğesinden bu yana ayrılan tüm nesneleri döker. @No__t-0 çağrısı gerçekleştiğinden, `DumpAllObjectsSince` Şu anda bellekte bulunan tüm nesneleri ve olmayan nesneleri döker.

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

Bir nesne dökümünden en fazla bilgi miktarını almak için, nesne dökümünü özelleştirmek üzere herhangi bir @no__t -1 ile türetilmiş nesnenin `Dump` üye işlevini geçersiz kılabilirsiniz.

@No__t-0 genel değişkenini küme ayraçları içinde gösterilen sayıya ayarlayarak, belirli bir bellek ayırma üzerinde bir kesme noktası ayarlayabilirsiniz. Programı yeniden çalıştırırsanız, bu ayırma gerçekleştiğinde hata ayıklayıcı yürütmeyi keser. Ardından, programınızın bu noktaya nasıl kullanıldığını görmek için çağrı yığınına bakabilirsiniz.

C çalışma zamanı kitaplığı, C çalışma zamanı ayırmaları için kullanabileceğiniz benzer bir [_Crtsetbreakkalloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)işlevine sahiptir.

[Bu konuda](#BKMK_In_this_topic)

#### <a name="BKMK_Interpreting_memory_dumps"></a>Bellek dökümlerini yorumlama
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

@No__t-0 Oluşturucusu, `CString` üye değişkenlerini başlatmak için kullanılan `char` işaretçileri olan üç bağımsız değişken alır. Bellek dökümünde, `CPerson` nesnesini üç nesne olmayan blok (3, 4 ve 5) ile birlikte görebilirsiniz. Bunlar `CString` üye değişkenlerinin karakterlerini tutar ve `CPerson` nesne yıkıcısı çağrıldığında silinmez.

Blok numarası 2 `CPerson` nesnesinin kendisidir. `$51A4`, bloğun adresini temsil eder ve [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)tarafından çağrıldığında `CPerson`:: `Dump` tarafından çıktı olan nesnenin içerikleri tarafından izlenir.

1\. Blok numarası 1 ' in sıra numarası ve boyutu nedeniyle `CString` çerçeve değişkeniyle ilişkili olduğunu tahmin edebilirsiniz. Bu, çerçeve `CString` değişkeninde karakter sayısıyla eşleşir. Çerçeve kapsam dışına geçtiğinde çerçevede ayrılan değişkenler otomatik olarak serbest bırakılır.

**Çerçeve değişkenleri**

Genel olarak, çerçeve değişkenleri kapsam dışına dönerek serbest bırakıldıklarından, çerçeve değişkenleriyle ilişkili yığın nesneleri hakkında endişelenmemelisiniz. Bellek Tanılama dökümlerinizin dağınıklığını önlemek için, çağrılarınızı `Checkpoint` ' a konumlandırmalı ve bu sayede, çerçeve değişkenlerinin kapsamı dışında olmaları gerekir. Örneğin, aşağıda gösterildiği gibi, önceki ayırma kodunun etrafına kapsam ayraçları yerleştirin:

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

Bazı ayırmaların nesne olduğunu (`CPerson` gibi) ve bazılarının nesne olmayan ayırmaları olduğunu unutmayın. "Nesne olmayan ayırmalar", `CObject` ' dan türetilmeyen nesneler için ayırmalar veya `char`, `int` veya `long` gibi temel C türlerinin tahsisatlarından alınmıştır. <strong>CObject ile</strong>türetilmiş sınıf, iç arabellekler gibi ek alan ayırırsa, bu nesneler hem nesne hem de nesne olmayan ayırmaları gösterir.

**Bellek sızıntılarını önlemek**

Yukarıdaki kodda, `CString` çerçeve değişkeniyle ilişkili bellek bloğunun otomatik olarak serbest bırakıldığına ve bellek sızıntısı olarak gösterilmediğine dikkat edin. Kapsam kurallarıyla ilişkili otomatik ayırmayı kaldırma, çerçeve değişkenleriyle ilişkili çoğu bellek sızıntılarını üstlenir.

Ancak yığında ayrılan nesneler için, bir bellek sızıntısını engellemek için nesneyi açıkça silmeniz gerekir. Önceki örnekte yer alan son bellek sızıntısını temizlemek için, yığında ayrılan `CPerson` nesnesini aşağıdaki gibi silin:

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

#### <a name="BKMK_Customizing_object_dumps"></a>Nesne dökümlerini özelleştirme
[CObject](/cpp/mfc/reference/cobject-class)'ten bir sınıf türettiğinizde, [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) kullandığınızda [Çıkış penceresinde](../ide/reference/output-window.md)nesneleri dökmek için `Dump` üye işlevini geçersiz kılabilirsiniz.

@No__t-0 işlevi, bir döküm bağlamına ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)) nesnenin üye değişkenlerinin metinsel gösterimini yazar. Döküm bağlamı bir g/ç akışına benzer. @No__t-2 ' ye veri göndermek için Append işlecini ( **<<** ) kullanabilirsiniz.

@No__t-0 işlevini geçersiz kıldığınızda, temel sınıf nesnesinin içeriğinin dökümünü yapmak için önce `Dump` ' in temel sınıf sürümünü çağırmanız gerekir. Ardından, türetilmiş sınıfınızın her bir üye değişkeni için bir metinsel açıklama ve değer çıkışı yapın.

@No__t-0 işlevinin bildirimi şöyle görünür:

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

Nesne dökümü yalnızca programınızda hata ayıklaması yaparken anlamlı olduğundan, `Dump` işlevinin bildirimi, bir **#ifdef _DEBUG/#endif** bloğu ile ayraç içine alınmıştır.

Aşağıdaki örnekte, `Dump` işlevi ilk olarak temel sınıfı için `Dump` işlevini çağırır. Ardından, her üye değişkeninin kısa bir açıklamasını ve üyenin değerini tanılama akışına yazar.

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

Döküm çıkışının nereye gidebileceği belirtmek için bir `CDumpContext` bağımsız değişkeni sağlamalısınız. MFC 'nin hata ayıklama sürümü, hata ayıklayıcıya çıktı gönderen `afxDump` adlı önceden tanımlanmış bir `CDumpContext` nesnesi sağlar.

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

## <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a>MFC hata ayıklama derlemesinin boyutunu azaltma
Büyük bir MFC uygulaması için hata ayıklama bilgileri çok miktarda disk alanı alabilir. Boyutunu azaltmak için şu yordamlardan birini kullanabilirsiniz:

1. /Z7 yerine [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format) SEÇENEĞINI kullanarak MFC kitaplıklarını yeniden derleyin **.** Bu seçenekler, tüm kitaplık için hata ayıklama bilgilerini içeren tek bir program veritabanı (PDB) dosyası oluşturur, artıklığı azaltır ve alan tasarrufu yapın.

2. MFC kitaplıklarını hata ayıklama bilgileri olmadan yeniden derleyin ( [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format) seçeneği). Bu durumda, hata ayıklama bilgilerinin bulunmaması, MFC kitaplık kodu içindeki çoğu hata ayıklayıcı tesislerini kullanmanızı önler, ancak MFC kitaplıklarının zaten kapsamlı bir şekilde ayıklandığından bu sorun olmayabilir.

3. Aşağıda açıklandığı gibi, seçilen modüller için hata ayıklama bilgileri ile kendi uygulamanızı oluşturun.

    [Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a>Seçilen modüller için hata ayıklama bilgileriyle bir MFC uygulaması oluşturma
MFC hata ayıklama kitaplıklarıyla seçili modüllerin oluşturulması, bu modüllerde adımlamayı ve diğer hata ayıklama olanaklarını kullanmanıza olanak sağlar. Bu yordam, projenin hata ayıklama ve sürüm yapılandırmalarının yanı sıra, aşağıdaki adımlarda açıklanan değişiklikleri tasarımda (ve ayrıca tam bir yayın derlemesi gerektiğinde "tümünü yeniden derle" seçeneğini de yapar).

1. Çözüm Gezgini, projeyi seçin.

2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

3. İlk olarak yeni bir proje yapılandırması oluşturacaksınız.

   1. **@No__t-1Proje > Özellik sayfaları** iletişim kutusunda **Configuration Manager** düğmesine tıklayın.

   2. [Configuration Manager iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), kılavuzdaki projenizi bulun. **Yapılandırma** sütununda **\<new... öğesini seçin. >** .

   3. [Yeni proje yapılandırması iletişim kutusunda](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), yeni yapılandırmanız Için, **Proje yapılandırma adı** kutusuna "kısmi hata ayıklama" gibi bir ad yazın.

   4. **Ayarları Şuradan Kopyala** listesinden **yayın**' ı seçin.

   5. **Yeni proje yapılandırması** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

   6. **Configuration Manager** iletişim kutusunu kapatın.

4. Şimdi tüm projenin seçeneklerini ayarlayacaksınız.

   1. **Özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörü altında **genel** kategorisini seçin.

   2. Proje ayarları kılavuzunda, **Proje Varsayılanları** ' nı genişletin (gerekirse).

   3. **Proje Varsayılanları**altında **MFC kullanımını**bulun. Geçerli ayar kılavuzun sağ sütununda görünür. Geçerli ayara tıklayın ve **MFC 'Yi statik bir kitaplıkta kullanmak**üzere değiştirin.

   4. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde, **C/C++**  klasörünü açın ve **Önişlemci**' yi seçin. Özellikler kılavuzunda **Önişlemci tanımlarını** bulun ve "ndebug" ÖĞESINI "_DEBUG" ile değiştirin.

   5. **Özellikler sayfaları** iletişim kutusunun sol bölmesinde, **bağlayıcı** klasörünü açın ve **giriş** kategorisini seçin. Özellikler kılavuzunda **ek bağımlılıklar**bulun. **Ek bağımlılıklar** ayarında "NAFXCWD" yazın. LIB "ve" LIBCMT. "

   6. Yeni derleme seçeneklerini kaydetmek ve **Özellik sayfaları** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. **Derle** menüsünde **yeniden oluştur**' u seçin. Bu, tüm hata ayıklama bilgilerini modüllerinizle kaldırır ancak MFC kitaplığını etkilemez.

6. Artık uygulamanızdaki seçili modüllere hata ayıklama bilgilerini geri eklemeniz gerekir. Kesme noktaları ayarlayabildiğinize ve yalnızca hata ayıklama bilgileriyle derlediğiniz modüllerde diğer hata ayıklayıcı işlevleri gerçekleştirebildiğinize unutmayın. Hata ayıklama bilgilerini dahil etmek istediğiniz her proje dosyası için aşağıdaki adımları uygulayın:

   1. Çözüm Gezgini, projenizin altında bulunan **kaynak dosyaları** klasörünü açın.

   2. Hata ayıklama bilgilerini ayarlamak istediğiniz dosyayı seçin.

   3. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

   4. **Özellik sayfaları** iletişim kutusundaki **yapılandırma ayarları** klasörü altında, **C++ C/** klasörünü açın ve **genel** kategorisini seçin.

   5. Özellikler kılavuzunda **hata ayıklama bilgileri biçimini bulun.**

   6. Hata ayıklama **bilgileri biçim** ayarlarına tıklayın ve hata ayıklama bilgileri için istediğiniz seçeneği (genellikle **/Zi**) seçin.

   7. Uygulama Sihirbazı tarafından oluşturulan bir uygulama kullanıyorsanız veya önceden derlenmiş üstbilgilere sahipseniz, önceden derlenmiş üstbilgileri kapatmanız veya diğer modülleri derlerken önce yeniden derlemeniz gerekir. Aksi takdirde, uyarı C4650 ve hata iletisi C2855 alırsınız. **@No__t-2proje > Özellikler** iletişim kutusundaki **önceden derlenmiş üst bilgileri oluştur/kullan** ayarını değiştirerek (**yapılandırma özellikleri** klasörü, **C/C++**  alt klasörü, **önceden derlenmiş), önceden derlenmiş üst bilgileri devre dışı bırakabilirsiniz. Üst bilgiler** kategorisi).

7. **Oluşturma** menüsünde, güncel olmayan proje dosyalarını yeniden derlemek için **Oluştur** ' u seçin.

   Bu konu başlığı altında açıklanan tekniğe alternatif olarak, her bir dosya için ayrı ayrı seçenekler tanımlamak üzere bir dış derleme görevleri dosyası kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarıyla bağlantı sağlamak için her modül için [_Hata ayıklama](/cpp/c-runtime-library/debug) bayrağını tanımlamanız gerekir. MFC sürüm kitaplıklarını kullanmak istiyorsanız, NDEBUG tanımlamanız gerekir. Dış makefiles yazma hakkında daha fazla bilgi için bkz. [NMAKE Başvurusu](/cpp/build/running-nmake).

   [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
[Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
