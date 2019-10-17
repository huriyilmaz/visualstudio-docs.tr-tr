---
title: C/C++ onaylama | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 154abe3d73fa71ac897f0442697196cd859f32bd
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435898"
---
# <a name="cc-assertions"></a>C/C++ Onayları
Bir onaylama deyimi, programınızdaki bir noktada doğru olması beklenen bir koşulu belirtir. Bu koşul doğru değilse, onaylama başarısız olur, programınızın yürütülmesi kesintiye uğrar ve [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Visual Studio, C++ aşağıdaki yapıları temel alan onay deyimlerini destekler:

- MFC programları için MFC onayları.

- ATL kullanan programlar için [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) .

- C çalışma zamanı kitaplığını kullanan programlar için CRT onaylamaları.

- Diğer C/C++ PROGRAMLARı için ANSI [onaylama işlevi](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) .

  Onaylama işlemlerini, mantık hatalarını yakalamak, bir işlemin sonuçlarını denetlemek ve işlenmeli test hata koşulları 'nı kullanabilirsiniz.

## <a name="BKMK_In_this_topic"></a>Bu konuda
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

## <a name="BKMK_How_assertions_work"></a>Onaylamalar nasıl çalışır?
Bir MFC veya C çalışma zamanı kitaplığı onaylaması nedeniyle hata ayıklayıcı başlatıldığında, kaynak kullanılabiliyorsa, hata ayıklayıcı onaylama işlemi gerçekleştiği kaynak dosyadaki noktaya gider. Onaylama iletisi hem [Çıkış penceresinde](../ide/reference/output-window.md) hem de **onaylama başarısız** iletişim kutusunda görünür. Daha sonra başvurmak üzere kaydetmek istiyorsanız, onay iletisini **Çıkış** penceresinden bir metin penceresine kopyalayabilirsiniz. **Çıkış** penceresinde diğer hata iletileri de bulunabilir. Onaylama hatasının nedenine ilişkin ipuçları sağladığından bu iletileri dikkatle inceleyin.

Geliştirme sırasında hataları algılamak için onaylamaları kullanın. Kural olarak, her varsayım için bir onaylama kullanın. Örneğin, bir bağımsız değişkenin NULL olmadığını varsaydıysanız, Bu varsayımını sınamak için bir onaylama işlemi kullanın.

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>Hata ayıklama ve sürüm Derlemeleriyle onaylama işlemleri
Onaylama deyimleri yalnızca `_DEBUG` tanımlanmışsa derlenir. Aksi takdirde, derleyici onayları null deyimler olarak değerlendirir. Bu nedenle, onay deyimleri son sürüm programınızda bir ek yük veya performans maliyeti vermez ve `#ifdef` yönergeleri kullanmaktan kaçınmanızı sağlar.

## <a name="BKMK_Side_effects_of_using_assertions"></a>Onayları kullanmanın yan etkileri
Kodunuza onaylama eklediğinizde, onayların yan etkileri olmadığından emin olun. Örneğin, `nM` değerini değiştiren aşağıdaki onay onayını göz önünde bulundurun:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

@No__t-0 ifadesi programınızın yayın sürümünde değerlendirilmediği için, `nM`, hata ayıklama ve sürüm sürümlerinde farklı değerlere sahip olur. MFC 'deki bu sorundan kaçınmak için `ASSERT` yerine [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) makrosunu kullanabilirsiniz. `VERIFY`, ifadeyi tüm sürümlerde değerlendirir ancak yayın sürümündeki sonucu denetlemez.

Bir işlevin değerlendirilmesi beklenmeyen yan etkilere sahip olabileceğinden, özellikle onaylama deyimlerinde işlev çağrıları kullanma konusunda dikkatli olun.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`myFnctn`, hem hata ayıklama hem de sürüm sürümlerinde  ' i çağırır, bu nedenle kullanılması kabul edilebilir. Ancak, @no__t 0 ' ı kullanmak, yayın sürümündeki gereksiz bir işlev çağrısının ek yükünü uygular.

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a>CRT onayları
CRTDBG. H üst bilgi dosyası [_onaylama ve _ASSERTE makrolarını](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) onaylama denetimi için tanımlar.

| Makroya | Sonuç |
|------------| - |
| `_ASSERT` | Belirtilen ifade FALSE olarak değerlendirilirse, `_ASSERT` ' ın dosya adı ve satır numarası. |
| `_ASSERTE` | @No__t-0 ile aynı ve onaylanan ifadenin dize temsili. |

`_ASSERTE`, yanlış olarak açılan onaylanan ifadeyi raporladığından daha güçlüdür. Bu, kaynak koda başvurulmadan sorunu belirlemek için yeterli olabilir. Ancak, uygulamanızın hata ayıklama sürümü, `_ASSERTE` kullanılarak onaylanan her bir ifade için bir dize sabiti içerecektir. Çok sayıda `_ASSERTE` makrosu kullanıyorsanız, bu dize ifadeleri önemli miktarda bellek alır. Bu, bir sorun olduğunu kanıtlar, belleği kaydetmek için `_ASSERT` kullanın.

@No__t-0 tanımlandığında, `_ASSERTE` makrosu aşağıdaki gibi tanımlanır:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Onaylanan ifade FALSE olarak değerlendirilirse, onaylama hatasını raporlamak için [_Crtdbgreport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) çağırılır (varsayılan olarak bir ileti iletişim kutusu kullanarak). İleti iletişim kutusunda **yeniden dene** ' yi seçerseniz `_CrtDbgReport` 1 döndürür ve `_CrtDbgBreak` `DebugBreak` aracılığıyla hata ayıklayıcısını çağırır.

### <a name="checking-for-heap-corruption"></a>Yığın bozulması denetleniyor
Aşağıdaki örnek, yığın bozulmasını denetlemek için [_Crtcheckmemory](/cpp/c-runtime-library/reference/crtcheckmemory) kullanır:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Işaretçi geçerliliği denetleniyor
Aşağıdaki örnek, belirli bir bellek aralığının okuma veya yazma için geçerli olduğunu doğrulamak için [_Crtıvalpointer](/cpp/c-runtime-library/reference/crtisvalidpointer) kullanır.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

Aşağıdaki örnek, bir işaretçinin yerel yığında belleğe işaret ettiğini doğrulamak için [_Crtıvalheappointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) kullanır (C çalışma zamanı kitaplığı 'nın bu örneği tarafından oluşturulan ve yönetilen yığın), bir dll kendi kitaplığı örneğine ve bu nedenle kendi yığınına sahip olabilir. Uygulama yığınının dışında). Bu onaylama yalnızca null veya sınırların dışında bir adresi değil, statik değişkenlerin, yığın değişkenlerinin ve diğer yerel olmayan belleğin işaretçilerini de işaretçiler.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Bellek bloğu denetleniyor
Aşağıdaki örnek, bir bellek bloğunun yerel yığında olduğunu ve geçerli bir blok türüne sahip olduğunu doğrulamak için [_Crtımemoryblock](/cpp/c-runtime-library/reference/crtismemoryblock) kullanır.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a>MFC onayları
MFC, onaylama denetimi için [onaylama](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) makrosunu tanımlar. Ayrıca, @no__t -2-türetilmiş bir nesnenin iç durumunu denetlemek için `MFC ASSERT_VALID` ve `CObject::AssertValid` yöntemlerini tanımlar.

MFC `ASSERT` makrosunun bağımsız değişkeni sıfır veya false olarak değerlendirilirse, makro program yürütmesini durdurur ve kullanıcıyı uyarır; Aksi takdirde, yürütme devam eder.

Bir onaylama başarısız olduğunda, bir ileti iletişim kutusunda kaynak dosyanın adı ve onaylama satır numarası gösterilir. İletişim kutusunda yeniden dene ' yi seçerseniz, [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) çağrısı yürütmenin hata ayıklayıcıya kesilmesine neden olur. Bu noktada, çağrının başarısız olduğunu anlamak için çağrı yığınını inceleyebilir ve diğer hata ayıklayıcı tesislerini kullanabilirsiniz. [Tam zamanında hata ayıklamayı](../debugger/just-in-time-debugging-in-visual-studio.md)etkinleştirdiyseniz ve hata ayıklayıcı zaten çalışmıyorsa, iletişim kutusu hata ayıklayıcıyı başlatabilir.

Aşağıdaki örnek, bir işlevin dönüş değerini denetlemek için `ASSERT` ' ın nasıl kullanılacağını gösterir:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

İşlev bağımsız değişkenlerinin tür denetimini sağlamak için [IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) IŞLEVIYLE birlikte onaylama kullanabilirsiniz:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

@No__t-0 makrosu yayın sürümünde kod üretmez. Yayın sürümündeki ifadeyi değerlendirmeniz gerekiyorsa, onaylama yerine [VERIFY](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) makrosunu kullanın.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID ve CObject:: AssertValid
[CObject:: AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) yöntemi, bir nesnenin iç durumunun çalışma zamanı denetimleri sağlar. @No__t-1 ' den sınıfınızı türettiğinizde `AssertValid` ' ı geçersiz kılmanız gerekli olmasa da, bunu yaparak sınıfınızı daha güvenilir hale getirebilirsiniz. `AssertValid` ' ın geçerli değerler içerdiğini doğrulamak için tüm nesnenin üye değişkenlerinin üzerinde onaylama işlemleri gerçekleştirmesi gerekir. Örneğin, işaretçi üye değişkenlerinin NULL olmadığını denetlemelidir.

Aşağıdaki örnek, `AssertValid` işlevinin nasıl bildirilemeyeceğini göstermektedir:

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

@No__t-0 ' ı geçersiz kıldığınızda, kendi kontrollerinizi gerçekleştirmeden önce `AssertValid` ' in temel sınıf sürümünü çağırın. Ardından, burada gösterildiği gibi, türetilmiş sınıfınıza özgü üyeleri denetlemek için onay makrosunu kullanın:

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

Üye değişkenlerinizin herhangi biri nesneleri depoladıysanız, iç geçerliliğini test etmek için `ASSERT_VALID` makrosunu kullanabilirsiniz (sınıfları `AssertValid` ' i geçersiz kıldıysanız).

Örneğin, bir [CObList](/cpp/mfc/reference/coblist-class) öğesini üye değişkenlerinden birinde depolayan bir sınıf @no__t (0) düşünün. @No__t-0 değişkeni, `m_DataList`, `CPerson` nesnelerinin bir koleksiyonunu saklar. @No__t-0 ' ın kısaltılmış bildirimi şuna benzer:

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

@No__t-1 ' deki `AssertValid` geçersiz kılma şuna benzer:

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

`CMyData`, veri üyesinde depolanan nesnelerin geçerliliğini sınamak için `AssertValid` mekanizmasını kullanır. @No__t-1 @no__t geçersiz kılma, kendi m_pDataList üye değişkeni için `ASSERT_VALID` makrosunu çağırır.

@No__t-0 sınıfı aynı zamanda `AssertValid` ' i geçersiz kıldığından, geçerlilik testi bu düzeyde durmaz. Bu geçersiz kılma, listenin iç durumunda ek geçerlilik testi gerçekleştirir. Bu nedenle, `CMyData` nesnesi üzerindeki bir geçerlilik testi, depolanan `CObList` liste nesnesinin iç durumları için ek geçerlilik testlerine yol açar.

Daha fazla iş sayesinde, listede depolanan `CPerson` nesnelerine yönelik geçerlilik testleri de ekleyebilirsiniz. @No__t-0 `CObList` ' den bir sınıf türetebilir ve `AssertValid` ' y i geçersiz kılabilirsiniz. Geçersiz kılmada `CObject::AssertValid` ' ı çağırır ve sonra listede `AssertValid` ' i çağırarak listede depolanan her bir @no__t 2 nesnesi üzerinde. Bu konunun başında gösterilen `CPerson` sınıfı zaten `AssertValid` ' i geçersiz kılar.

Bu, hata ayıklama için derleme yaparken güçlü bir mekanizmadır. Daha sonra yayın için derleme yaptığınızda mekanizma otomatik olarak kapatılır.

### <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid sınırlamaları
Tetiklenen bir onaylama, nesnenin kesinlikle hatalı olduğunu ve yürütmenin durmayacağını gösterir. Ancak, onaylaması olmaması yalnızca bir sorun bulunamadığını gösterir, ancak nesnenin iyi olduğu garanti edilmez.

[Bu konuda](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a>Onayları kullanma

### <a name="BKMK_Catching_logic_errors"></a>Mantık hatalarını yakalama
Programınızın mantığına göre doğru olması gereken bir koşul üzerinde onay ayarlayabilirsiniz. Bir mantık hatası oluşmadığı takdirde onaylama etkisizdir.

Örneğin, bir kapsayıcıda gaz molecules benzetimi olduğunu ve `numMols` değişkeninin toplam molecules sayısını temsil ettiğini varsayalım. Bu sayı sıfırdan küçük olamaz, bu nedenle buna benzer bir MFC onaylama deyimi ekleyebilirsiniz:

```cpp
ASSERT(numMols >= 0);
```

Ya da şunun gibi bir CRT onay ekleyebilirsiniz:

```cpp
_ASSERT(numMols >= 0);
```

Programınız doğru çalışıyorsa, bu deyimler hiçbir şey yapmaz. Bir mantık hatası `numMols` ' dan küçük olmasına neden olur, ancak onaylama işlemi programınızın yürütülmesini durdurur ve [onaylama başarısız Iletişim kutusunu](../debugger/assertion-failed-dialog-box.md)görüntüler.

[Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a>Sonuçlar denetleniyor
Onaylamalar, sonuçları hızlı bir görsel incelemeden daha belirgin olmayan test işlemleri için değerlidir.

Örneğin, `mols` tarafından işaret edilen bağlantılı listenin içeriğine göre `iMols` değişkenini güncelleştiren aşağıdaki kodu göz önünde bulundurun:

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

@No__t-0 ile sayılan motacules sayısı, her zaman motacules, `numMols` ' in toplam sayısından küçük veya eşit olmalıdır. Döngünün görsel denetlemesi bunun durum olarak olduğunu göstermez, bu nedenle bu koşul için test etme döngüsünden sonra bir onaylama deyimi kullanılır.

[Bu konuda](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a>İşlenmemiş hataları bulma
Kodunuzun herhangi bir hata işlendiği bir noktada hata koşullarını test etmek için onaylamaları kullanabilirsiniz. Aşağıdaki örnekte, bir grafik yordamı başarılı için bir hata kodu veya sıfır döndürür.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Hata işleme kodu düzgün çalışıyorsa, onaylamaya ulaşılmadan önce hatanın işlenmesi ve `myErr` ' ı sıfıra sıfırlanması gerekir. @No__t-0 başka bir değere sahipse onaylama başarısız olur, program çöktüler ve [onaylama başarısız Iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görüntülenir.

Ancak, onaylama deyimleri hata işleme kodu için bir değiştirme değildir. Aşağıdaki örnek, son sürüm kodundaki sorunlara yol açabilecek bir onaylama deyimi gösterir:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Bu kod, hata koşulunu işlemek için assertion deyimine bağımlıdır. Sonuç olarak, `myGraphRoutine` tarafından döndürülen tüm hata kodları son sürüm kodunda yakalanacaktır.

[Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.

- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Koddaki Onaylamalar](../debugger/assertions-in-managed-code.md)