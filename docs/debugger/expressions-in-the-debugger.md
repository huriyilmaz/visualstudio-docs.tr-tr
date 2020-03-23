---
title: Hata ayıklamadaki ifadeler | Microsoft Dokümanlar
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ab66f288ad8442b6f2b5aab3499e2c1f3857632
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302170"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklama daki ifadeler
Visual Studio hata ayıklayıcı, **QuickWatch** iletişim kutusuna, **İzleme** penceresine veya **Hemen** penceresine bir ifade girdiğinizde çalışan ifade değerlendiricileriçerir. İfade değerlendiriciler, **Kesme Noktaları** penceresinde ve hata ayıklayıcıdaki diğer birçok yerde de iş başındadır.

Aşağıdaki bölümlerde Visual Studio tarafından desteklenen diller için ifade değerlendirme sınırlamaları açıklanmaktadır.

## <a name="f-expressions-are-not-supported"></a>F# ifadeleri desteklenmiyor
F# ifadeleri tanınmaz. F# kodunu hata ayıklıyorsanız, ifadeleri hata ayıklama penceresine veya iletişim kutusuna girmeden önce ifadelerinizi C# sözdizimine çevirmeniz gerekir. İfadeleri F#'dan C#'a çevirdiğinizde, C#'ın `==` eşitliği test etmek için işleci kullandığını, F#'nın ise tekini `=`kullandığını unutmayın.

## <a name="c-expressions"></a>C++ İfadeleri
C++'da ifadelerle bağlam işleçlerini kullanma hakkında bilgi için [bkz.](../debugger/context-operator-cpp.md)

### <a name="unsupported-expressions-in-c"></a>C++'da Desteklenmeyen İfadeler

#### <a name="constructors-destructors-and-conversions"></a>Yapıcılar, yıkıcılar ve dönüşümler
Bir nesne için açık veya kapalı olarak bir oluşturucu veya yıkıcı çağıramazsınız. Örneğin, aşağıdaki ifade açıkça bir oluşturucu çağırır ve bir hata iletisi ile sonuçlanır:

```C++
my_date( 2, 3, 1985 )
```

Dönüştürmenin hedefi bir sınıfsa, dönüşüm işlevini çağıramazsınız. Böyle bir dönüştürme bir nesnenin yapımını içerir. Örneğin, dönüşüm `myFraction` işlevi işleci `CFraction` `FixedPoint`tanımlayan bir , örneği ise, aşağıdaki ifade bir hatayla sonuçlanır:

```C++
(FixedPoint)myFraction
```

Yeni veya silme operatörlerini arayamaz sınız. Örneğin, aşağıdaki ifade desteklenmez:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Önişlemci Makroları
Hata ayıklamada önişlemci makroları desteklenmez. Örneğin, bir sabit `VALUE` şu şekilde `#define VALUE 3`bildirilirse: , `VALUE` **Watch** penceresinde kullanamazsınız. Bu sınırlamayı önlemek için, mümkün olduğunca enums ve fonksiyonlar ile 's değiştirmelisiniz. `#define`

### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma
Bildirimleri `using namespace` kullanamazsınız.  Geçerli ad alanının dışında bir tür adı veya değişkene erişmek için tam nitelikli adı kullanmanız gerekir.

### <a name="anonymous-namespaces"></a>Anonim ad alanları
Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, saat `test` penceresine ekleyemezsiniz:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Durumu korumak için hata ayıklama içsel işlevleri kullanma
Hata ayıklama içsel işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevlerini çağırmanın bir yolunu verir.

Hata ayıklama içsel fonksiyonlar:

- Güvenli olduğu garanti edilir: hata ayıklama içsel işlevi yürütmek debugged ediliyor işlemi bozmaz.

- Yan etkilere ve fonksiyon değerlendirmesine izin verilmeyen senaryolarda bile tüm ifadelere izin verilir.

- Normal işlev çağrılarının mümkün olmadığı senaryolarda (örneğin, bir minidump hata ayıklama gibi) çalışın.

  Hata ayıklama içsel işlevler de ifadeleri değerlendirmeyi daha kullanışlı hale getirebilir. Örneğin, `strncmp(str, "asd")` bir kesme noktası durumunda yazmak çok `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`daha kolaydır. )

|Alan|İç işlevler|
|----------|-------------------------|
|**Dize uzunluğu**|[strlen, wcslen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Dize karşılaştırması**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Dize arama**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29), [GetLastError](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Bu işlevler, Windows 8'de çalıştırılmak üzere debugged olan işlemi gerektirir. Windows 8 aygıtından oluşturulan döküm dosyalarının hata ayıklanması, Visual Studio bilgisayarının Windows 8 çalıştırılmasını da gerektirir. Ancak, bir Windows 8 aygıtını uzaktan hata ayıklıyorsanız, Visual Studio bilgisayarı Windows 7 çalıştırıyor olabilir.|
|**Çeşitli**|__log2 // Belirtilen bir tamsaın günlük tabanını verir, en yakın alt tamsayıya yuvarlanır.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx // Eşzamanlılık::dizi<>::operator[index<>] ve operator(index<>)<br /><br />ConcurrencyArray_OperatorBracket_int // Eşzamanlılık::dizi<>::operator(int, int, ...)<br /><br />ConcurrencyArray_OperatorBracket_tidx // Eşzamanlılık::dizi<>::operator[tiled_index<>] ve operatör(tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx // Eşzamanlılık::array_view<>::operator[index<>] ve operator(index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int // Eşzamanlılık::array_view<>::operator(int, int, ...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx // Eşzamanlılık::array_view<>::operator[tiled_index<>] ve operatör(tiled_index<>)<br /><br />TreeTraverse_Init // Yeni bir ağaç geçişini başlatma<br /><br />TreeTraverse_Next // Ağaçtaki düğümleri döndürür<br /><br />TreeTraverse_Skip // Bekleyen bir ağaç geçişinde düğümleri atlar'|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - Desteklenmeyen İfadeler

- İşaretçileri veya kullanıcı tanımlı dökümleri içeren dökümler desteklenmez.

- Nesne karşılaştırması ve atama desteklenmez.

- Aşırı yüklenen operatörler ve aşırı yüklü işlevler desteklenmez.

- Kutulama ve unboxing desteklenmez.

- `Sizeof`işleci desteklenmez.

## <a name="c---unsupported-expressions"></a>C# - Desteklenmeyen İfadeler

### <a name="dynamic-objects"></a>Dinamik Nesneler
Statik olarak dinamik olarak yazılan hata ayıklama ifadelerinde değişkenler kullanabilirsiniz. Uygulayan <xref:System.Dynamic.IDynamicMetaObjectProvider> nesneler İzleme penceresinde değerlendirildiğinde Dinamik Görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerini düzenlemeye izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve`*=`

- Sayısal dökümler ve yazı bağımsız değişken dökümleri de dahil olmak üzere birçok döküm

- Yöntem ikiden fazla bağımsız değişkeni olan çağrıları

- İkiden fazla bağımsız değişkeni olan özellik getters

- Bağımsız değişkenleri olan özellik ayarlayıcıları

- Dizin leyiciye atama

- Boolean `&&` operatörleri ve`||`

### <a name="anonymous-methods"></a>Anonim Yöntemler
Yeni anonim yöntemlerin oluşturulması desteklenmez.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Desteklenmeyen İfadeler

### <a name="dynamic-objects"></a>Dinamik Nesneler
Statik olarak dinamik olarak yazılan hata ayıklama ifadelerinde değişkenler kullanabilirsiniz. Watch penceresinde uygulanan <xref:System.Dynamic.IDynamicMetaObjectProvider> nesneler değerlendirildiğinde Dinamik Görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerini düzenlemeye izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve`*=`

- Sayısal dökümler ve yazı bağımsız değişken dökümleri de dahil olmak üzere birçok döküm

- Yöntem ikiden fazla bağımsız değişkeni olan çağrıları

- İkiden fazla bağımsız değişkeni olan özellik getters

- Bağımsız değişkenleri olan özellik ayarlayıcıları

- Dizin leyiciye atama

- Boolean `&&` operatörleri ve`||`

### <a name="local-constants"></a>Yerel Sabitler
Yerel sabitler desteklenmez.

### <a name="import-aliases"></a>Diğer Adları İthalat
Alma takma adları desteklenmez.

### <a name="variable-declarations"></a>Değişken Bildirimler
Hata ayıklama pencerelerinde açık yeni değişkenler bildiremezsiniz. Ancak, **Hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumuna göre kapsamlıdır ve hata ayıklama nın dışında erişilemez. Örneğin, deyim `o = 5` örtülü olarak yeni bir `o` değişken oluşturur ve 5 değerini ona atar. Tür hata ayıklama tarafından çıkarılamıyorsa, bu tür örtük değişkenler **nesne** türündendir.

### <a name="unsupported-keywords"></a>Desteklenmeyen Anahtar Kelimeler

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Ad alanı veya modül düzeyindeanahtar kelimeler, gibi `End Sub` veya `Module`.

## <a name="see-also"></a>Ayrıca bkz.
- [C++'da Biçimlendirme](../debugger/format-specifiers-in-cpp.md)
- [Bağlam İşlemesi (C++)](../debugger/context-operator-cpp.md)
- [C'deki Biçimlendirmeler #](../debugger/format-specifiers-in-csharp.md)
- [Sözde Değişkenler](../debugger/pseudovariables.md)
