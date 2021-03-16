---
title: C/C++ Onayları | Microsoft Docs
description: C/C++ onaylamaları 'nın Visual Studio Hata ayıklamasında nasıl çalıştığı hakkında bilgi edinin. Bir onaylama işlemi, programınızdaki bir noktada doğru olması beklenen bir koşulu belirtir.
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
ms.workload:
- cplusplus
ms.openlocfilehash: e347bd8de6342a79d7523a1085f0e40cad8b0cbf
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571499"
---
# <a name="cc-assertions"></a>C/C++ Onayları

Bir onaylama deyimi, programınızdaki bir noktada doğru olması beklenen bir koşulu belirtir. Bu koşul doğru değilse, onaylama başarısız olur, programınızın yürütülmesi kesintiye uğrar ve [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Visual Studio, aşağıdaki yapıları temel alan C++ onaylama deyimlerini destekler:

- MFC programları için MFC onayları.

- ATL kullanan programlar için [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) .

- C çalışma zamanı kitaplığını kullanan programlar için CRT onaylamaları.

- Diğer C/C++ programları için ANSI [onaylama işlevi](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) .

  Onaylama işlemlerini, mantık hatalarını yakalamak, bir işlemin sonuçlarını denetlemek ve işlenmeli test hata koşulları 'nı kullanabilirsiniz.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda

[Onaylamalar nasıl çalışır?](#BKMK_How_assertions_work)

[Hata ayıklama ve sürüm Derlemeleriyle onaylama işlemleri](#BKMK_Assertions_in_Debug_and_Release_builds)

[Onayları kullanmanın yan etkileri](#BKMK_Side_effects_of_using_assertions)

[CRT onayları](#BKMK_CRT_assertions)

[MFC onayları](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID ve CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [AssertValid sınırlamaları](#BKMK_Limitations_of_AssertValid)

  [Onayları kullanma](#BKMK_Using_assertions)

- [Mantık hatalarını yakalama](#BKMK_Catching_logic_errors)

- [Sonuçlar denetleniyor](#BKMK_Checking_results_)

- [İşlenmemiş hataları bulma](#BKMK_Testing_error_conditions_)

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Onaylamalar nasıl çalışır?

Bir MFC veya C çalışma zamanı kitaplığı onaylaması nedeniyle hata ayıklayıcı başlatıldığında, kaynak kullanılabiliyorsa, hata ayıklayıcı onaylama işlemi gerçekleştiği kaynak dosyadaki noktaya gider. Onaylama iletisi hem [Çıkış penceresinde](../ide/reference/output-window.md) hem de **onaylama başarısız** iletişim kutusunda görünür. Daha sonra başvurmak üzere kaydetmek istiyorsanız, onay iletisini **Çıkış** penceresinden bir metin penceresine kopyalayabilirsiniz. **Çıkış** penceresinde diğer hata iletileri de bulunabilir. Onaylama hatasının nedenine ilişkin ipuçları sağladığından bu iletileri dikkatle inceleyin.

Geliştirme sırasında hataları algılamak için onaylamaları kullanın. Kural olarak, her varsayım için bir onaylama kullanın. Örneğin, bir bağımsız değişkenin NULL olmadığını varsaydıysanız, Bu varsayımını sınamak için bir onaylama işlemi kullanın.

[Bu konuda](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Hata ayıklama ve sürüm Derlemeleriyle onaylama işlemleri

Onaylama deyimleri yalnızca tanımlanmışsa derlenir `_DEBUG` . Aksi takdirde, derleyici onayları null deyimler olarak değerlendirir. Bu nedenle, onay deyimleri son sürüm programınızda bir ek yük veya performans maliyeti vermez ve yönergeleri kullanmaktan kaçınmanızı sağlar `#ifdef` .

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Onayları kullanmanın yan etkileri

Kodunuza onaylama eklediğinizde, onayların yan etkileri olmadığından emin olun. Örneğin, bu değeri değiştiren aşağıdaki onay onayını göz önünde bulundurun `nM` :

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

`ASSERT`İfade programınızın yayın sürümünde değerlendirilmediği için, `nM` hata ayıklama ve yayın sürümlerinde farklı değerlere sahip olur. MFC 'deki bu sorundan kaçınmak için yerine [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) makrosunu kullanabilirsiniz `ASSERT` . `VERIFY` tüm sürümlerde ifadeyi değerlendirir ancak yayın sürümünde sonucu denetlemez.

Bir işlevin değerlendirilmesi beklenmeyen yan etkilere sahip olabileceğinden, özellikle onaylama deyimlerinde işlev çağrıları kullanma konusunda dikkatli olun.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY``myFnctn`hem hata ayıklama hem de sürüm sürümlerinde çağrılır, bu nedenle kullanılması kabul edilebilir. Ancak, kullanma, `VERIFY` yayın sürümünde gereksiz bir işlev çağrısının yükünü uygular.

[Bu konuda](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> CRT onayları

CRTDBG. H üstbilgi dosyası, onaylama denetimi için [_assert ve _ASSERTE makrolarını](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) tanımlar.

| Makroya | Sonuç |
|------------| - |
| `_ASSERT` | Belirtilen ifade FALSE olarak değerlendirilirse, öğesinin dosya adı ve satır numarası `_ASSERT` . |
| `_ASSERTE` | İle aynı `_ASSERT` , ve onaylanan ifadenin dize temsili. |

`_ASSERTE` , yanlış olarak kapatılmış olan onaylanan ifadeyi bildirdiğinden daha güçlüdür. Bu, kaynak koda başvurulmadan sorunu belirlemek için yeterli olabilir. Ancak, uygulamanızın hata ayıklama sürümü kullanılarak onaylanan her bir ifade için bir dize sabiti içerecektir `_ASSERTE` . Çok sayıda makro kullanıyorsanız `_ASSERTE` , bu dize ifadeleri önemli miktarda bellek alır. Bu, bir sorun olduğunu kanıtlar, `_ASSERT` belleği kaydetmek için kullanın.

`_DEBUG`Tanımlandığında, `_ASSERTE` makro aşağıdaki gibi tanımlanır:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Onaylanan ifade FALSE olarak değerlendirilirse, onaylama hatasını raporlamak için [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) çağırılır (varsayılan olarak bir ileti iletişim kutusu kullanarak). İleti iletişim kutusunda **yeniden dene** ' yi seçerseniz, `_CrtDbgReport` 1 döndürür ve `_CrtDbgBreak` hata ayıklayıcıyı aracılığıyla çağırır `DebugBreak` .

Tüm onayları geçici olarak devre dışı bırakmanız gerekiyorsa [_CtrSetReportMode](/cpp/c-runtime-library/reference/crtsetreportmode)kullanın.

### <a name="checking-for-heap-corruption"></a>Yığın bozulması denetleniyor

Aşağıdaki örnek, yığın bozulmasını denetlemek için [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) kullanır:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Işaretçi geçerliliği denetleniyor

Aşağıdaki örnek, belirli bir bellek aralığının okuma veya yazma için geçerli olduğunu doğrulamak için [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) kullanır.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

Aşağıdaki örnek, bir işaretçinin yerel yığında belleğe işaret ettiğini doğrulamak için [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) kullanır (C çalışma zamanı kitaplığı 'nın bu örneği tarafından oluşturulan ve yönetilen yığın), bir dll, kendi kitaplığı örneğine ve bu nedenle uygulama yığınının dışında kendi yığınına sahip olabilir. Bu onaylama yalnızca null veya sınırların dışında bir adresi değil, statik değişkenlerin, yığın değişkenlerinin ve diğer yerel olmayan belleğin işaretçilerini de işaretçiler.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Bellek bloğu denetleniyor

Aşağıdaki örnek, bir bellek bloğunun yerel yığında olduğunu ve geçerli bir blok türüne sahip olduğunu doğrulamak için [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) kullanır.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Bu konuda](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> MFC onayları

MFC, onaylama denetimi için [onaylama](/previous-versions/ew16s3zc(v=vs.140)) makrosunu tanımlar. Ayrıca, `MFC ASSERT_VALID` `CObject::AssertValid` bir türetilmiş nesnenin iç durumunu denetlemek için ve yöntemlerini tanımlar `CObject` .

MFC makrosunun bağımsız değişkeni `ASSERT` sıfır veya false olarak değerlendirilirse, makro program yürütmesini durdurur ve kullanıcıyı uyarır; Aksi takdirde yürütme devam eder.

Bir onaylama başarısız olduğunda, bir ileti iletişim kutusunda kaynak dosyanın adı ve onaylama satır numarası gösterilir. İletişim kutusunda yeniden dene ' yi seçerseniz, [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) çağrısı yürütmenin hata ayıklayıcıya kesilmesine neden olur. Bu noktada, çağrının başarısız olduğunu anlamak için çağrı yığınını inceleyebilir ve diğer hata ayıklayıcı tesislerini kullanabilirsiniz. [Tam zamanında hata ayıklamayı](../debugger/just-in-time-debugging-in-visual-studio.md)etkinleştirdiyseniz ve hata ayıklayıcı zaten çalışmıyorsa, iletişim kutusu hata ayıklayıcıyı başlatabilir.

Aşağıdaki örnek, `ASSERT` bir işlevin dönüş değerini denetlemek için nasıl kullanılacağını gösterir:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

İşlev bağımsız değişkenlerinin tür denetimini sağlamak için [IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) IŞLEVIYLE birlikte onaylama kullanabilirsiniz:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT`Makro yayın sürümünde kod üretmez. Yayın sürümündeki ifadeyi değerlendirmeniz gerekiyorsa, onaylama yerine [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) makrosunu kullanın.

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID ve CObject:: AssertValid

[CObject:: AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) yöntemi, bir nesnenin iç durumunun çalışma zamanı denetimleri sağlar. `AssertValid`Sınıfınızı ' den türettiğinizde geçersiz kılmanız gerekli olmasa da `CObject` , bunu yaparak sınıfınızı daha güvenilir hale getirebilirsiniz. `AssertValid` geçerli değerler içerdiklerinden emin olmak için nesnenin tüm üye değişkenlerine onay gerçekleştirmelidir. Örneğin, işaretçi üye değişkenlerinin NULL olmadığını denetlemelidir.

Aşağıdaki örnek, bir işlevin nasıl bildirilemeyeceğini göstermektedir `AssertValid` :

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

Geçersiz kıldığınızda `AssertValid` , `AssertValid` kendi kontrollerinizi gerçekleştirmeden önce temel sınıf sürümünü çağırın. Ardından, burada gösterildiği gibi, türetilmiş sınıfınıza özgü üyeleri denetlemek için onay makrosunu kullanın:

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

Üye değişkenlerinizin herhangi biri nesneleri depoladıysanız, `ASSERT_VALID` iç geçerliliğini test etmek için makroyu kullanabilirsiniz (sınıfları geçersiz kılınsın `AssertValid` ).

Örneğin, bir `CMyData` [CObList](/cpp/mfc/reference/coblist-class) öğesini üye değişkenlerinden birinde depolayan bir sınıfı düşünün. `CObList`Değişkeni, `m_DataList` bir nesne koleksiyonunu depolar `CPerson` . Kısaltılmış bildirimi `CMyData` Şuna benzer:

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

`AssertValid`Geçersiz kılma `CMyData` Şuna benzer:

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

`CMyData` , `AssertValid` kendi veri üyesinde depolanan nesnelerin geçerliliğini test etmek için mekanizmasını kullanır. Geçersiz kılma `AssertValid` , `CMyData` `ASSERT_VALID` makroyu kendi m_pDataList üye değişkeni için çağırır.

Bu düzeyde, sınıf `CObList` da geçersiz kılındığından geçerlilik testi durdurulmaz `AssertValid` . Bu geçersiz kılma, listenin iç durumunda ek geçerlilik testi gerçekleştirir. Bu nedenle, bir nesne üzerindeki bir geçerlilik testi, `CMyData` depolanan liste nesnesinin iç durumları için ek geçerlilik testlerine yol açar `CObList` .

Daha fazla iş sayesinde, `CPerson` listede depolanan nesneler için de geçerlilik testleri ekleyebilirsiniz. Sınıfından bir sınıf türetebilirsiniz `CPersonList` `CObList` ve geçersiz kılabilirsiniz `AssertValid` . Geçersiz kılmada, listede `CObject::AssertValid` depolanan her bir nesneye çağrı yapan ve sonra listede yineleme yapılır `AssertValid` `CPerson` . `CPerson`Bu konunun başlangıcında gösterilen sınıf zaten geçersiz kılar `AssertValid` .

Bu, hata ayıklama için derleme yaparken güçlü bir mekanizmadır. Daha sonra yayın için derleme yaptığınızda mekanizma otomatik olarak kapatılır.

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> AssertValid sınırlamaları
Tetiklenen bir onaylama, nesnenin kesinlikle hatalı olduğunu ve yürütmenin durmayacağını gösterir. Ancak, onaylaması olmaması yalnızca bir sorun bulunamadığını gösterir, ancak nesnenin iyi olduğu garanti edilmez.

[Bu konuda](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Onayları kullanma

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Mantık hatalarını yakalama

Programınızın mantığına göre doğru olması gereken bir koşul üzerinde onay ayarlayabilirsiniz. Bir mantık hatası oluşmadığı takdirde onaylama etkisizdir.

Örneğin, bir kapsayıcıda gaz molecules benzetimi olduğunu ve değişkeni de `numMols` Toplam molecules sayısını temsil ettiğini varsayalım. Bu sayı sıfırdan küçük olamaz, bu nedenle buna benzer bir MFC onaylama deyimi ekleyebilirsiniz:

```cpp
ASSERT(numMols >= 0);
```

Ya da şunun gibi bir CRT onay ekleyebilirsiniz:

```cpp
_ASSERT(numMols >= 0);
```

Programınız doğru çalışıyorsa, bu deyimler hiçbir şey yapmaz. Ancak bir mantık hatası sıfırdan küçük olmasına neden oluyorsa `numMols` , onaylama işlemi programınızın yürütülmesini durdurur ve [onaylama başarısız iletişim kutusunu](../debugger/assertion-failed-dialog-box.md)görüntüler.

[Bu konuda](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Sonuçlar denetleniyor

Onaylamalar, sonuçları hızlı bir görsel incelemeden daha belirgin olmayan test işlemleri için değerlidir.

Örneğin, aşağıdaki kodu göz önünde bulundurun. Bu, değişkeni `iMols` tarafından işaret edilen bağlantılı listenin içeriğine göre güncelleştirir `mols` :

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

Sayılan motacules sayısı `iMols` , her zaman motacules 'in toplam sayısından küçük veya buna eşit olmalıdır `numMols` . Döngünün görsel denetlemesi bunun durum olarak olduğunu göstermez, bu nedenle bu koşul için test etme döngüsünden sonra bir onaylama deyimi kullanılır.

[Bu konuda](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> İşlenmemiş hataları bulma

Kodunuzun herhangi bir hata işlendiği bir noktada hata koşullarını test etmek için onaylamaları kullanabilirsiniz. Aşağıdaki örnekte, bir grafik yordamı başarılı için bir hata kodu veya sıfır döndürür.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Hata işleme kodu düzgün çalışıyorsa, `myErr` onaylamaya ulaşılmadan önce hatanın işlenmesi ve sıfıra sıfırlanması gerekir. `myErr`Başka bir değer varsa, onaylama başarısız olur, program çöktüler ve [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Ancak, onaylama deyimleri hata işleme kodu için bir değiştirme değildir. Aşağıdaki örnek, son sürüm kodundaki sorunlara yol açabilecek bir onaylama deyimi gösterir:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Bu kod, hata koşulunu işlemek için assertion deyimine bağımlıdır. Sonuç olarak, tarafından döndürülen tüm hata kodları `myGraphRoutine` son sürüm kodunda yakalanacaktır.

[Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen koddaki Onaylamalar](../debugger/assertions-in-managed-code.md)