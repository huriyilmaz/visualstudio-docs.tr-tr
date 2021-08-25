---
title: Hata Ayıklayıcıdaki İfadeler | Microsoft Docs
description: Visual Studio hata ayıklayıcısında değerlendiricileri ifadesi tarafından hangi dil ifadelerinin desteklenmediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/24/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7db52fff8d2e952c0f0d591845d0c644e8212e3f
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785955"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısındaki ifadeler
Visual Studio hata ayıklayıcı, **quickwatch** iletişim kutusunda, **gözcü** penceresinde veya **anında** pencereye bir ifade girdiğinizde çalışan ifade değerlendiricileri içerir. Değerlendiricileri ifadesi Ayrıca **kesme noktaları** penceresinde ve hata ayıklayıcıda birçok diğer yerde de çalışır.

Aşağıdaki bölümlerde, Visual Studio tarafından desteklenen diller için ifade değerlendirmesinin sınırlamaları açıklanmaktadır.

## <a name="f-expressions-are-not-supported"></a>F # ifadeleri desteklenmez
F # ifadeleri tanınmıyor. F # kodunda hata ayıklaması yapıyorsanız, ifadeleri bir hata ayıklayıcı penceresine veya iletişim kutusuna girmeden önce ifadelerinizi C# sözdizimine çevirmeniz gerekir. F # ' dan C# ' A ifade çevirirken, C# ' nin `==` eşitlik için test etmek üzere Işlecini kullandığını unutmayın, f # Single öğesini kullanır `=` .

## <a name="c-expressions"></a>C++ Ifadeleri
C++ içindeki ifadelerle bağlam işleçlerini kullanma hakkında daha fazla bilgi için bkz. [Bağlam işleci (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>C++ ' da desteklenmeyen Ifadeler

#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, Yıkıcılar ve dönüştürmeler
Açıkça veya örtük olarak bir nesne için bir Oluşturucu ya da yıkıcı çağrılamaz. Örneğin, aşağıdaki ifade açıkça bir oluşturucuyu çağırır ve bir hata iletisiyle sonuçlanır:

```C++
my_date( 2, 3, 1985 )
```

Dönüştürmenin hedefi bir sınıf ise, bir dönüştürme işlevi çağrılamaz. Böyle bir dönüştürme bir nesnenin oluşturulmasını içerir. Örneğin, `myFraction` `CFraction` dönüştürme işlevi işlecini tanımlayan bir örneğidir, `FixedPoint` aşağıdaki ifade bir hatayla sonuçlanır:

```C++
(FixedPoint)myFraction
```

New veya delete işleçlerini çağrılamaz. Örneğin, aşağıdaki ifade desteklenmez:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Önişlemci makroları
Önişlemci makroları hata ayıklayıcıda desteklenmez. Örneğin, bir sabit değer `VALUE` olarak bildirilirse `#define VALUE 3` , `VALUE` **Gözcü** penceresinde kullanamazsınız. Bu sınırlamayı önlemek için, `#define` mümkün olan her durumda Enum ve işlevlerle değiştirmelisiniz.

### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma
`using namespace`Bildirimleri kullanamazsınız.  Geçerli ad alanı dışındaki bir tür adına veya değişkenine erişmek için tam adı kullanmanız gerekir.

### <a name="anonymous-namespaces"></a>Anonim ad alanları
Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, `test` Gözcü penceresine ekleyemezsiniz:

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

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Durumu korumak için hata ayıklayıcı iç işlevlerini kullanma
Hata ayıklayıcı iç işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevlerini çağırmak için bir yol sağlar.

Hata ayıklayıcı iç işlevleri:

- Güvenli olduğu garanti edilir: bir hata ayıklayıcı iç işlevinin yürütülmesi, hataları ayıklanan işlemi bozmaz.

- Yan etkileri ve işlev değerlendirmesinin izin verilmediği senaryolarda bile tüm ifadelerde izin verilir.

- Bir mini döküm dosyasında hata ayıklama gibi normal işlev çağrılarının mümkün olmadığı senaryolarda çalışın.

  Hata ayıklayıcı iç işlevleri ayrıca değerlendirme ifadelerin daha kullanışlı olmasını sağlayabilir. Örneğin, `strncmp(str, "asd")` bir kesme noktası koşulunda daha kolay yazılması çok daha kolaydır `str[0] == 'a' && str[1] == 's' && str[2] == 'd'` . )

|Alan|İç işlevler|
|----------|-------------------------|
|**Dize uzunluğu**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Dize karşılaştırması**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsıcmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnıcmp, wcsnıcmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Dize arama**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[Codecodeproxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](/previous-versions/bb432242(v=vs.85)), [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[Roınspectcapturedstackbacktrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [windowscomparestringordinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [windowsgetstringlen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [windowsgetstrıngrawbuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Bu işlevler, hata ayıklamakta olan işlemin Windows 8 üzerinde çalışıyor olmasını gerektirir. Windows 8 bir cihazdan oluşturulan döküm dosyalarının hata ayıklaması, Visual Studio bilgisayarın Windows 8 çalıştırılmasını gerektirir. ancak, Windows 8 bir cihazın uzaktan hata ayıklaması yapıyorsanız, Visual Studio bilgisayar Windows 7 ' yi çalıştırıyor olabilir.<br />`WindowsGetStringLen`ve `WindowsGetStringRawBuffer` yalnızca kaynak düzeyindeki yürütme motoru (EE) tarafından kullanılır.|
|**Çeşitli**|**__log2** -belirtilen bir tamsayının, en yakın küçük tamsayıya yuvarlanmış 2 günlük tabanını döndürür.<br /><br />**__findNonNull** -bir işaretçiler dizisini arar ve ilk null olmayan öğenin dizinini döndürür.<br />-Parameters: (1) dizideki ilk öğenin Işaretçisi (void *), (2) dizi boyutu (işaretsiz int). <br /> -Dönüş değerleri: (1) dizide null olmayan ilk öğenin 0 tabanlı dizini veya bulunmazsa-1. <br /> <br /> * * DecodeHString**-BIR HString değerini biçimlendirmek için yardımcı işlev. hstring değerini yığından kapatır, EE dizenin nerede bulunduğunu söylemek için kullanabileceği bir stringınfo yapısının baytlarını çıkarır. Bu yalnızca EE tarafından dahili olarak kullanılır; Kullanıcı tarafından doğrudan çağrı için kullanılamaz.<br /><br />**Decodewınrtkısıttedexception** -kısıtlanmış açıklamayı almak Için bir WinRT kısıtlı özel durumunun kodunu çözer.<br />-Parameters: (1) kısıtlanmış başvuru dizesini temsil eden, null ile sonlandırılmış bir dizenin karakterleri.<br />-Dönüş değeri: gösterilecek gerçek hata iletisini içeren null ile sonlandırılmış bir dizenin karakterleri.<br /><br />**Dynamiccast** -dynamic_cast uygular.<br />-Parametreler: (1) Cast nesne Işaretçisi.<br />-Veri öğeleri: bir Cdynamicbir veri nesnesi, karşılık gelen Executeıntrinsic () yönergesinin veri öğesi olarak ilişkilendirilmelidir. Veri öğesi, ' den ve ' a dönüştürtiğimiz türü kodluyor, ayrıca bir Natvis ifadesini değerlendiriyoruz olup olmadığı gibi, (Tanılamayı sonsuz özyineleme bozmak için gereklidir).<br />-Dönüş değeri: (1) nesneye yönelik bir işaretçi, doğru türe atama, veya nesne dönüştürme işlemi doğru türün bir örneği değilse NULL.<br /><br />Bir sınıf üyesinin değerini dinamik olarak almak için **Dynamicmemberlookup** yardımcı işlevi<br /><br />Bir ortam bloğunun uzunluğunu (karakter) almak için **Getenvblocklength** yardımcı işlevi.  $Env için kullanılır.<br /><br />Stdext:: hash_map için **Stdext_HashMap_Int_OperatorBracket_idx** -operator [].  Varsayılan karma işlevi ' int ' anahtarıyla varsayar.  Değeri döndürür. [] İç işleci yalnızca Hashtable 'dan var olan öğelerin alınmasını destekler-bu, bellek ayırma gibi istenmeyen karmaşıklığa dahil olmak üzere tabloya yeni öğe eklemeyi desteklemez.  Ancak, [] işleci, tabloda bulunan bir anahtarla ilişkili değeri değiştirmek için kullanılabilir.<br />-Stack parametreleri: (1) stdext:: hash_map nesnesinin adresi, (2) tabloya anahtar (int), (3) işlev uygulamasının arama yapması için gereken alan farklarını belirten bir HashMapPdb yapısı.  Simgelere doğrudan erişim uzak tarafta kullanılamadığından bu gereklidir.<br />-Dönüş değerleri: (1) anahtar tabloda ise, anahtara karşılık gelen değerin adresi.  Aksi takdirde, NULL.<br /><br />**Std_UnorderedMap_Int_OperatorBracket_idx** -std:: unordered_map, karma işlevin farklı olması dışında, stdext:: hash_map ile aynı şekilde çalışır.<br /><br />**ConcurrencyArray_OperatorBracket_idx** //concurrency:: Array<>:: operator [Dizin<>] ve işleç (Dizin<>)<br /><br />**ConcurrencyArray_OperatorBracket_int** //concurrency:: Array<>:: operator (int, int,...)<br /><br />**ConcurrencyArray_OperatorBracket_tidx** //concurrency:: Array<>:: operator [tiled_index<>] and işleci (tiled_index<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_idx** //concurrency:: array_view<>:: operator [Dizin<>] ve işleç (Dizin<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_int** //concurrency:: array_view<>:: operator (int, int,...)<br /><br />**ConcurrencyArrayView_OperatorBracket_tidx** //concurrency:: array_view<>:: operator [tiled_index<>] and işleci (tiled_index<>)<br /><br />**TreeTraverse_Init** -yeni bir ağaç geçişi başlatır. <br />-Stack parametreleri: (1) kök düğümün adresi, (2) en yüksek derinlik kullanımı için Ipucu.  Bunun ötesinde bir derinlikte bulunan öğeler daha sonra işlenmek üzere kuyruğa taşınır.<br />-Altyordam parametreleri: (1) düğüm geçerliliği (isteğe bağlı).<br />-Dönüş değerleri: (1) ağaç geçişi durumunun kodlanması için donuk bir bayt dizisi.<br /><br />**TreeTraverse_Next** -bekleyen bir ağaç geçiş işleminden düğümleri alır.<br />-Stack parametreleri: (1) ağaç geçişinin durumunu temsil eden donuk bayt dizisi, (2) getirilecek düğüm sayısı.<br />-Altyordam parametreleri (TreeTraverse_Init ()) çağrısıyla eşleşmelidir: (1) sol alt, (2) sağ alt, (3) düğüm geçerliliği (isteğe bağlı).<br />-Dönüş değerleri: (1) getirilen düğüm sayısı (yani, düğümlerden sonra, bu nedenle ilk olarak bir yere itilmiş olabilir). İstenenden daha az düğüm getirildiyse, bu, ağacın sonu anlamına gelir. (2) getirilen her düğüm için, düğümün adresi. (3) ağaç geçişinin yeni durumunu kodlayan, opak bayt dizisi<br /><br />**TreeTraverse_Skip** - Bekleyen bir ağaç geçişteki düğümleri atlar.<br />- Yığın Parametreleri: (1) Ağaç geçiş durumunu temsil eden opak byte dizisi, (2) Atlanır düğüm sayısı.<br />- Alt yol parametreleri (aynı numaralayıcıda sonraki Next() çağrılarında eşleşmeli): (1) sol alt, (2) sağ alt, (3) düğüm geçerliliği (isteğe bağlı).<br />- Dönüş değerleri: (1) Gerçekten atlanan öğe sayısı (istenenden daha az olabilir), (2) Ağaç geçişinin yeni durumunu kodlayan opak bayt dizisi|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - Desteklenmeyen İfadeler

- İşaretçileri veya kullanıcı tanımlı cast'ları içeren cast'lar desteklenmiyor.

- Nesne karşılaştırması ve ataması desteklenmiyor.

- Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmiyor.

- Kutulama ve kutudan açma desteklenmiyor.

- `Sizeof` işleci desteklenmiyor.

## <a name="c---unsupported-expressions"></a>C# - Desteklenmeyen İfadeler

### <a name="dynamic-objects"></a>Dinamik Nesneler
Dinamik olarak statik olarak türüne sahip hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulama izleme penceresi, dinamik görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerinin düzenlenmesine izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmiyor:

- Bileşik işleçler `+=` `-=` , , , `%=` `/=` ve `*=`

- Sayısal tür dönüştürmeler ve tür bağımsız değişken dönüştürmeleri de dahil olmak üzere birçok tür dönüştürme

- İkiden fazla bağımsız değişken ile yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip özellik alan

- Bağımsız değişkenlerle özellik ayarları

- Dizine atama

- Boole işleçleri `&&` ve `||`

### <a name="anonymous-methods"></a>Anonim Yöntemler
Yeni anonim yöntemlerin oluşturulması desteklenmiyor.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Desteklenmeyen İfadeler

### <a name="dynamic-objects"></a>Dinamik Nesneler
Dinamik olarak statik olarak türüne sahip hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> uygulama içinde değerlendir izleme penceresi Dinamik Görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerinin düzenlenmesine izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmiyor:

- Bileşik işleçler `+=` `-=` , , , `%=` `/=` ve `*=`

- Sayısal tür dönüştürmeler ve tür bağımsız değişken dönüştürmeleri de dahil olmak üzere birçok tür dönüştürme

- İkiden fazla bağımsız değişken ile yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip özellik alan

- Bağımsız değişkenlerle özellik ayarları

- Dizine atama

- Boole işleçleri `&&` ve `||`

### <a name="local-constants"></a>Yerel Sabitler
Yerel sabitler desteklenmiyor.

### <a name="import-aliases"></a>Diğer Adları İçeri Aktarma
İçeri aktarma diğer adları desteklenmiyor.

### <a name="variable-declarations"></a>Değişken Bildirimleri
Hata ayıklayıcı pencerelerde açık yeni değişkenleri bildiresiniz. Ancak, Anında penceresinde yeni örtülü değişkenler **atabilirsiniz.** Bu örtülü değişkenlerin kapsamı hata ayıklama oturumuna göredir ve hata ayıklayıcı dışından erişilemez. Örneğin, deyimi örtülü `o = 5` olarak yeni bir değişken oluşturur ve `o` 5 değerini buna atar. Tür hata ayıklayıcı tarafından **atılamayacaksa,** bu tür örtülü değişkenler Object türündedir.

### <a name="unsupported-keywords"></a>Desteklenmeyen Anahtar Sözcükler

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

- veya gibi ad alanı veya modül düzeyi anahtar `End Sub` `Module` sözcükler.

## <a name="see-also"></a>Ayrıca bkz.
- [C++'ta Biçim Belirleyicileri](../debugger/format-specifiers-in-cpp.md)
- [Bağlam İşleci (C++)](../debugger/context-operator-cpp.md)
- [C'de Biçim Belirleyicileri #](../debugger/format-specifiers-in-csharp.md)
- [Sözde Değişkenler](../debugger/pseudovariables.md)