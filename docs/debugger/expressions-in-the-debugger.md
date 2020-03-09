---
title: Hata Ayıklayıcıdaki İfadeler | Microsoft Docs
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
ms.sourcegitcommit: c8b979a56c95e43cf8ae92b6c3c9570db59a8e58
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78925383"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısındaki ifadeler
Visual Studio hata ayıklayıcı, **QuickWatch** iletişim kutusunda, **Gözcü** penceresinde veya **anında** pencereye bir ifade girdiğinizde çalışan ifade değerlendiricileri içerir. Değerlendiricileri ifadesi Ayrıca **kesme noktaları** penceresinde ve hata ayıklayıcıda birçok diğer yerde de çalışır.

Aşağıdaki bölümlerde, Visual Studio tarafından desteklenen diller için ifade değerlendirmesinin sınırlamaları açıklanmaktadır.

## <a name="f-expressions-are-not-supported"></a>F#ifadeler desteklenmiyor
F#ifadeler tanınmıyor. Kod hata ayıklaması F# yapıyorsanız, ifadeleri bir hata ayıklayıcı penceresine veya iletişim kutusuna C# girmeden önce ifadelerinizi sözdizimine çevirmeniz gerekir. İfadelerini F# C#' den ' a çevirirken, tek `=`C# F# kullandığında eşitlik için test etmek üzere `==` işlecini kullandığını unutmayın.

## <a name="c-expressions"></a>C++İfadelerde
İçindeki C++ifadelerle bağlam işleçlerini kullanma hakkında daha fazla bilgi için bkz. [Bağlam işleciC++()](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>İçinde desteklenmeyen IfadelerC++

#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, Yıkıcılar ve dönüştürmeler
Açıkça veya örtük olarak bir nesne için bir Oluşturucu ya da yıkıcı çağrılamaz. Örneğin, aşağıdaki ifade açıkça bir oluşturucuyu çağırır ve bir hata iletisiyle sonuçlanır:

```C++
my_date( 2, 3, 1985 )
```

Dönüştürmenin hedefi bir sınıf ise, bir dönüştürme işlevi çağrılamaz. Böyle bir dönüştürme bir nesnenin oluşturulmasını içerir. Örneğin, `myFraction` dönüştürme işlevi işleci `FixedPoint`tanımlayan `CFraction`bir örneğidir, aşağıdaki ifade bir hatayla sonuçlanır:

```C++
(FixedPoint)myFraction
```

New veya delete işleçlerini çağrılamaz. Örneğin, aşağıdaki ifade desteklenmez:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Önişlemci makroları
Önişlemci makroları hata ayıklayıcıda desteklenmez. Örneğin, bir sabit `VALUE` şöyle bildirilirse: `#define VALUE 3`, **izleme** penceresinde `VALUE` kullanamazsınız. Bu sınırlamayı önlemek için `#define`, mümkün olan her durumda Enum ve işlevlerle değiştirmelisiniz.

### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma
`using namespace` bildirimleri kullanamazsınız.  Geçerli ad alanı dışındaki bir tür adına veya değişkenine erişmek için tam adı kullanmanız gerekir.

### <a name="anonymous-namespaces"></a>Anonim ad alanları
Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, izleme penceresine `test` ekleyemezsiniz:

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

### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Durumu korumak için hata ayıklayıcı iç işlevlerini kullanma
Hata ayıklayıcı iç işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevleri çağırmak için bir yol sağlar.

Hata ayıklayıcı iç işlevleri:

- Güvenli olduğu garanti edilir: bir hata ayıklayıcı iç işlevinin yürütülmesi, hataları ayıklanan işlemi bozmaz.

- Yan etkileri ve işlev değerlendirmesinin izin verilmediği senaryolarda bile tüm ifadelerde izin verilir.

- Bir mini döküm dosyasında hata ayıklama gibi normal işlev çağrılarının mümkün olmadığı senaryolarda çalışın.

  Hata ayıklayıcı iç işlevleri ayrıca değerlendirme ifadelerin daha kullanışlı olmasını sağlayabilir. Örneğin, `strncmp(str, "asd")` kesme noktasında `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`daha kolay yazılması çok daha kolaydır. )

|Alan|İç işlevler|
|----------|-------------------------|
|**Dize uzunluğu**|[strlen, wcslen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Dize karşılaştırması**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsıcmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnıcmp, wcsnıcmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Dize arama**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win**|[Codecodeproxy](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29), [GetLastError](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[Roınspectcapturedstackbacktrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [windowscomparestringordinal](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [windowsgetstringlen](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [windowsgetstrıngrawbuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Bu işlevler, hata ayıklamakta olan işlemin Windows 8 üzerinde çalışıyor olmasını gerektirir. Windows 8 cihazından oluşturulan döküm dosyalarının hata ayıklaması, Visual Studio bilgisayarının Windows 8 çalıştırıyor olmasını da gerektirir. Ancak, Windows 8 cihazının uzaktan hata ayıklaması yapıyorsanız, Visual Studio bilgisayarı Windows 7 çalıştırıyor olabilir.|
|**Çeşitli**|__log2//, belirtilen bir tamsayının, en yakın küçük tamsayıya yuvarlanmış 2 günlük tabanı döndürür.<br /><br />__findNonNull, DecodeHString, Decodewinrtkısıttedexception, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//concurrency:: Array < >:: operator [Dizin < >] ve işleç (Dizin < >)<br /><br />ConcurrencyArray_OperatorBracket_int//concurrency:: Array < >:: operator (int, int,...)<br /><br />ConcurrencyArray_OperatorBracket_tidx//concurrency:: Array < >:: operator [tiled_index < >] and işleci (tiled_index < >)<br /><br />ConcurrencyArrayView_OperatorBracket_idx//concurrency:: array_view < >:: operator [Index < >] and işleci (Dizin < >)<br /><br />ConcurrencyArrayView_OperatorBracket_int//concurrency:: array_view < >:: operator (int, int,...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx//concurrency:: array_view < >:: operator [tiled_index < >] and işleci (tiled_index < >)<br /><br />Yeni bir ağaç geçişi TreeTraverse_Init//başlatır<br /><br />Bir ağaçtaki düğümleri TreeTraverse_Next//döndürür<br /><br />Bekleyen bir ağaç geçişinin içindeki düğümleri TreeTraverse_Skip//atlıyor|

## <a name="ccli---unsupported-expressions"></a>C++/CLı-desteklenmeyen Ifadeler

- İşaretçileri veya Kullanıcı tanımlı yayınları içeren yayınlar desteklenmez.

- Nesne karşılaştırma ve atama desteklenmiyor.

- Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmez.

- Kutulama ve kutudan çıkarma desteklenmez.

- `Sizeof` işleci desteklenmiyor.

## <a name="c---unsupported-expressions"></a>C#-Desteklenmeyen Ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulayan nesneler izleme penceresi değerlendirildiğinde dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=`, `-=`, `%=`, `/=`ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- `&&` ve `||` Boole işleçleri

### <a name="anonymous-methods"></a>Anonim Yöntemler
Yeni anonim yöntemlerin oluşturulması desteklenmez.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic-desteklenmeyen Ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulayan nesneler izleme penceresi değerlendirildiğinde dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=`, `-=`, `%=`, `/=`ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- `&&` ve `||` Boole işleçleri

### <a name="local-constants"></a>Yerel sabitler
Yerel sabitler desteklenmez.

### <a name="import-aliases"></a>Diğer adları içeri aktar
İçeri aktarma diğer adları desteklenmez.

### <a name="variable-declarations"></a>Değişken bildirimleri
Hata ayıklayıcı Windows 'da açık yeni değişkenler bildiremezsiniz. Bununla birlikte, **hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumunun kapsamına alınır ve hata ayıklayıcının dışında erişilebilir değildir. Örneğin, `o = 5` örtük olarak `o` yeni bir değişken oluşturur ve 5 değerini bu değere atar. Türü hata ayıklayıcı tarafından çıkarsanmadığı takdirde bu tür örtük değişkenler **Object** türündedir.

### <a name="unsupported-keywords"></a>Desteklenmeyen anahtar sözcükler

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

- `End Sub` veya `Module`gibi ad alanı veya modül düzeyi anahtar sözcükleri.

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Dilinde Biçim Belirticileri](../debugger/format-specifiers-in-cpp.md)
- [Bağlam İşleci (C++)](../debugger/context-operator-cpp.md)
- [C# Dilinde Biçim Belirticileri](../debugger/format-specifiers-in-csharp.md)
- [Sözde değişkenler](../debugger/pseudovariables.md)
