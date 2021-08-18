---
title: C/C++ Onaylamaları | Microsoft Docs
description: Hata ayıklamada C/C++ onaylarının nasıl Visual Studio okuyun. Onay, programda bir noktada doğru olmasını beklediğiniz bir koşulu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed7f138b41cc71cd4964bb50e3358e020905355
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129772"
---
# <a name="cc-assertions"></a>C/C++ Onayları

Assertion deyimi, programda bir noktada doğru olmasını beklediğiniz bir koşulu belirtir. Bu koşul doğru olmazsa onay başarısız olur, program yürütmesi kesintiye uğrar ve Onaylama Başarısız [iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Visual Studio aşağıdaki yapıları temel alan C++ onaylama deyimlerini destekler:

- MFC programları için MFC onaylamaları.

- ATL kullanan programlar için [ATLASSERT.](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert)

- C çalışma zamanı kitaplığını kullanan programlar için CRT onayları.

- Diğer C/C++ programları için ANSI [assert](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) işlevi.

  Onayları kullanarak mantık hatalarını yakalayabilir, bir işlem sonuçlarını kontrol eder ve işlen bir hata koşullarını test edin.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konu başlığında

[Onaylar nasıl çalışır?](#BKMK_How_assertions_work)

[Hata Ayıklama ve Yayın derlemeleri onayları](#BKMK_Assertions_in_Debug_and_Release_builds)

[Onayları kullanmanın yan etkileri](#BKMK_Side_effects_of_using_assertions)

[CRT onaylamaları](#BKMK_CRT_assertions)

[MFC onaylamaları](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID ve CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [AssertValid sınırlamaları](#BKMK_Limitations_of_AssertValid)

  [Onayları kullanma](#BKMK_Using_assertions)

- [Mantıksal hataları yakalama](#BKMK_Catching_logic_errors)

- [Sonuçları denetleme](#BKMK_Checking_results_)

- [İşlenemeyen hataları bulma](#BKMK_Testing_error_conditions_)

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Onaylar nasıl çalışır?

Hata ayıklayıcı bir MFC veya C çalışma zamanı kitaplığı onaylaması nedeniyle durdurulursa, kaynak kullanılabilirse hata ayıklayıcı, onayların kaynak dosyada bulunduğu noktaya gider. Onay iletisi hem Çıkış penceresinde hem [de Onay](../ide/reference/output-window.md) Başarısız oldu **iletişim kutusunda** görünür. Daha sonra başvuru için kaydetmek istediğiniz onay **iletiyi** Çıkış penceresinden bir metin penceresine kopyaabilirsiniz. Çıkış **penceresi** başka hata iletileri de içerebilir. Onaylama hatasının nedeni hakkında ipuçları sağlayan bu iletileri dikkatli bir şekilde inceleyin.

Geliştirme sırasında hataları algılamak için onayları kullanın. Kural olarak, her varsayım için bir onay kullanın. Örneğin, bir bağımsız değişkenin NULL olmadığını varsayın, bu varsayımı test etmek için bir onay kullanın.

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Hata Ayıklama ve Yayın derlemeleri onayları

Assertion deyimleri yalnızca `_DEBUG` tanımlanmışsa derlenmiş olur. Aksi takdirde, derleyici onayları null deyimler olarak kabul ediyor. Bu nedenle, onay deyimleri son Yayın programınıza ek yük veya performans maliyeti uygulamaz ve yönergelerini `#ifdef` kullanmamanızı sağlar.

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Onayları kullanmanın yan etkileri

Kodunuza onaylar eklerken, onayların yan etkilerine sahip olmadığını emin olun. Örneğin, değeri değiştiren aşağıdaki onaylamayı göz önünde `nM` bulun:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

İfade `ASSERT` programınız Yayın sürümünde değerlendirilmez, çünkü Hata Ayıklama ve Yayın `nM` sürümlerinde farklı değerlere sahip olacak. MFC'de bu sorunu önlemek için yerine [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) makrosu `ASSERT` kullanabilirsiniz. `VERIFY` ifadeyi tüm sürümlerde değerlendirir, ancak Yayın sürümünde sonucu denetlemez.

Onay deyimlerinde işlev çağrılarını kullanırken özellikle dikkatli olun çünkü bir işlevin değerlendirilmesi beklenmeyen yan etkilere neden olabilir.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` hem `myFnctn` Hata Ayıklama hem de Yayın sürümlerinde çağrısı yapılan bu nedenle kullanımı kabul edilebilir. Ancak, kullanmak `VERIFY` Sürüm sürümünde gereksiz bir işlev çağrısının ek yükünü getirir.

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> CRT onaylamaları

The CRTDBG. H üst bilgi [dosyası, onay _ASSERT için _ASSERTE ve kaynak](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) makrolarını tanımlar.

| Makro | Sonuç |
|------------| - |
| `_ASSERT` | Belirtilen ifade FALSE olarak değerlendirilirse dosya adı ve satır `_ASSERT` numarası. |
| `_ASSERTE` | ile aynı `_ASSERT` artı, onay yapılan ifadenin dize gösterimi. |

`_ASSERTE` daha güçlü çünkü false olduğu ortaya çıkan onaylandı ifadesini raporlar. Bu, kaynak koda başvurulmadan sorunu tanımlamak için yeterli olabilir. Ancak, uygulamanıza hata ayıklama sürümü kullanılarak onay yapılan her ifade için bir dize sabiti `_ASSERTE` içerir. Çok sayıda makro `_ASSERTE` kullanıyorsanız, bu dize ifadeleri önemli miktarda bellek alır. Bu bir sorun olduğunu kanıtlarsa, bellek tasarrufu `_ASSERT` yapmak için kullanın.

tanımlandığı `_DEBUG` zaman `_ASSERTE` makro aşağıdaki gibi tanımlanır:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Onay verilen ifade FALSE olarak değerlendirilirse, [onay _CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) (varsayılan olarak bir ileti iletişim kutusu kullanılarak) bildirecek şekilde çağrılır. İleti iletişim kutusunda **Yeniden Dene'yi** seçerseniz, `_CrtDbgReport` 1 döndürür ve `_CrtDbgBreak` üzerinden hata ayıklayıcıyı `DebugBreak` arar.

Tüm onayları geçici olarak devre dışı bırakmanız gerekirse, [_CtrSetReportMode.](/cpp/c-runtime-library/reference/crtsetreportmode)

### <a name="checking-for-heap-corruption"></a>Yığın Bozulması Denetimi

Aşağıdaki örnekte, [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) bozulma olup oluğu kontrol etmek için _CrtCheckMemory kullanır:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>İşaretçi Geçerliliğini Denetleme

Aşağıdaki örnekte, [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) aralığın okuma veya yazma için geçerli olduğunu doğrulamak için _CrtIsValidPointer 2.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

Aşağıdaki [örnekte, _CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) yerel yığında belleğe işaret eden bir işaretçiyi (C çalışma zamanı kitaplığının bu örneği tarafından oluşturulan ve yönetilen yığın) doğrulamak için _CrtIsValidHeapPointer kullanır; bir DLL kendi kitaplığı örneğine ve dolayısıyla uygulama yığınının dışında kendi yığınına sahip olabilir). Bu onay yalnızca null veya sınır dışı adresleri değil, statik değişkenlerin, yığın değişkenlerinin ve diğer yerel olmayan belleğin işaretçilerini de yakalar.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Bellek Bloğu denetleme

Aşağıdaki örnek, [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) bloğun yerel yığında olduğunu ve geçerli bir blok türüne sahip olduğunu doğrulamak için bir bellek bloğu kullanır.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> MFC onaylamaları

MFC onay denetimi [için ASSERT](/previous-versions/ew16s3zc(v=vs.140)) makrosu tanımlar. Ayrıca türetilmiş bir `MFC ASSERT_VALID` nesnenin `CObject::AssertValid` iç durumunu denetlemeye için ve yöntemlerini `CObject` tanımlar.

MFC makros un bağımsız değişkeni sıfır veya yanlış olarak değerlendirilirse, makro program yürütmesini durdurarak kullanıcıya uyarı verir; aksi `ASSERT` takdirde yürütme devam eder.

Onay başarısız olduğunda, kaynak dosyanın adını ve onay satırı numarasını gösteren bir ileti iletişim kutusu görüntülenir. İletişim kutusunda Yeniden Dene'yi seçerseniz [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) çağrısı, yürütmenin hata ayıklayıcıda kesmeye neden olur. Bu noktada, çağrı yığınını inceler ve onaylamanın neden başarısız olduğunu belirlemek için diğer hata ayıklayıcı olanaklarını kullanabilirsiniz. Tam zamanında [hata ayıklamayı etkinleştirdiysek](../debugger/just-in-time-debugging-in-visual-studio.md)ve hata ayıklayıcı zaten çalışmıyorsa, iletişim kutusu hata ayıklayıcıyı başlatabilirsiniz.

Aşağıdaki örnekte, işlevinin dönüş `ASSERT` değerini kontrol etmek için nasıl kullanabileceğiniz gösterir:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

İŞLEV bağımsız değişkenlerinin tür [denetimi sağlamak için ASSERT'ı IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) işleviyle birlikte kullanabilirsiniz:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

Makro `ASSERT` Yayın sürümünde kod üretmez. İfadeyi Yayın sürümünde değerlendirmeniz gerekirse ASSERT yerine [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) makrosu kullanın.

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID ve CObject::AssertValid

[CObject::AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) yöntemi, bir nesnenin iç durumunun çalışma zamanı denetimlerini sağlar. sınıfından türeterek geçersiz kılmanız gerekmasa da, bunu yaparak `AssertValid` `CObject` sınıfınızı daha güvenilir hale siniz. `AssertValid` , geçerli değerler içerdiğini doğrulamak için nesnenin tüm üye değişkenlerini onaylar gerçekleştirmesi gerekir. Örneğin, işaretçi üye değişkenlerinin NULL olmadığını denetlemesi gerekir.

Aşağıdaki örnekte, bir işlevin nasıl bildir olduğu `AssertValid` gösterir:

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

'ı geçersiz `AssertValid` kılarak kendi denetimlerinizi gerçekleştirmeden `AssertValid` önce temel sınıf sürümünü çağırmanız gerekir. Ardından, burada gösterildiği gibi türetilen sınıfınıza özgü üyeleri kontrol etmek için ASSERT makrosu kullanın:

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

Üye değişkenlerinden herhangi biri nesneleri depolarsa, iç geçerliliklerini test etmek için makroyu `ASSERT_VALID` kullanabilirsiniz (sınıfları geçersiz kıldısa). `AssertValid`

Örneğin, bir `CMyData` [CObList'i](/cpp/mfc/reference/coblist-class) üye değişkenlerinden biri içinde depolar bir sınıf düşünün. `CObList`değişkeni, `m_DataList` bir nesne koleksiyonunu `CPerson` depolar. kısaltılmış bildirimi şu `CMyData` şekildedir:

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

içinde `AssertValid` geçersiz kılma şu `CMyData` şekildedir:

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` , `AssertValid` veri üyesinde depolanan nesnelerin geçerliliğini test etmek için mekanizmasını kullanır. geçersiz kılma, `AssertValid` `CMyData` kendi üye değişkeni için `ASSERT_VALID` makroyu m_pDataList çağırır.

Geçerlilik testi bu düzeyde durmaz çünkü sınıfı da `CObList` geçersiz `AssertValid` kılar. Bu geçersiz kılma, listenin iç durumu üzerinde ek geçerlilik testi gerçekleştirir. Bu nedenle, bir nesnede geçerlilik testi, depolanan liste nesnesinin iç durumları için `CMyData` ek geçerlilik testlerine `CObList` neden olur.

Daha fazla çalışmayla, listede depolanan nesneler için `CPerson` de geçerlilik testleri ekleyebilirsiniz. sınıfından bir sınıf türetmek ve `CPersonList` geçersiz `CObList` `AssertValid` kılmak. Geçersiz kılmada, çağrısı `CObject::AssertValid` ve ardından listede depolanan her nesne üzerinde `AssertValid` çağırarak listede `CPerson` yinelersiniz. Bu `CPerson` konunun başında gösterilen sınıfı zaten geçersiz `AssertValid` kılar.

Bu, hata ayıklama için derleme sırasında güçlü bir mekanizmadır. Daha sonra yayın için derlemeyi tamamlarken mekanizma otomatik olarak kapanır.

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> AssertValid sınırlamaları
Tetiklenen onay, nesnenin kesinlikle kötü olduğunu ve yürütmenin durdurulur olduğunu gösterir. Ancak, onay eksikliği yalnızca hiçbir sorun bulunamadı olduğunu gösterir, ancak nesnenin iyi olduğu garanti edilemez.

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Onayları kullanma

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Mantıksal hataları yakalama

Program mantığına göre doğru olması gereken bir koşula onay ekleyebilirsiniz. Bir mantık hatası oluşmadıkça onaylamanın hiçbir etkisi olmaz.

Örneğin, bir kapsayıcıdaki gaz moleküllerinin simülasyonlarını taklit ettiğini ve değişkenin toplam molekül `numMols` sayısını temsil ettiğini varsayalım. Bu sayı sıfırdan küçük olamaz, bu nedenle aşağıdaki gibi bir MFC onay deyimi dahil olabilir:

```cpp
ASSERT(numMols >= 0);
```

Veya aşağıdaki gibi bir CRT onaylaması dahil olabilir:

```cpp
_ASSERT(numMols >= 0);
```

Programınız düzgün şekilde çalışıyorsa bu deyimler hiçbir şey yapmaz. Ancak, bir mantık hatası sıfırdan küçük bir hataya neden oluyorsa, onay programınız yürütmeyi durdurur ve Onaylama Başarısız İletişim `numMols` [Kutusunu görüntüler.](../debugger/assertion-failed-dialog-box.md)

[Bu konu başlığında](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Sonuçları denetleme

Onaylar, sonuçları hızlı bir görsel incelemeden net olmayan test işlemleri için değerlidir.

Örneğin, değişkeni tarafından işaret eden bağlantılı listenin içeriğine göre `iMols` güncelleştirmeye devam eden aşağıdaki kodu `mols` düşünün:

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

tarafından sayan moleküllerin sayısı her zaman toplam molekül sayısından küçük veya bu `iMols` sayıya eşit `numMols` olmalı. Döngüyü görsel olarak inceleme, bunun mutlaka böyle olacağını göstermez, bu nedenle bu koşulu test etmek için döngüden sonra bir assertion deyimi kullanılır.

[Bu konu başlığında](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> İşlenemeyen hataları bulma

Onayları kullanarak kodunuzun herhangi bir hatanın iş olması gereken bir noktadaki hata koşullarını test edin. Aşağıdaki örnekte, bir grafik yordamı başarı için bir hata kodu veya sıfır döndürür.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Hata işleme kodu düzgün şekilde çalışırsa, onay ulaşmadan önce hata iş olmalı ve `myErr` sıfıra sıfırlanır. Başka `myErr` bir değere sahipse onay başarısız olur, program durdurulur ve Onaylama Başarısız [İletişim Kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Ancak assertion deyimleri, hata işleme kodunun yerini tutamaz. Aşağıdaki örnek, son sürüm kodunda sorunlara yol açacak bir onay deyimini gösterir:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Bu kod, hata koşullarını işlemek için assertion deyimini kullandırıyor. Sonuç olarak, tarafından döndürülen tüm hata `myGraphRoutine` kodu son sürüm kodunda iş geri döndürülecek.

[Bu konu başlığında](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Onaylar](../debugger/assertions-in-managed-code.md)