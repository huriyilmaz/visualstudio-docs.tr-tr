---
title: Hata ayıklayıcısında ifadeler | Microsoft Docs
description: Hata ayıklayıcısında ifade değerlendiricileri tarafından hangi dil ifadelerini Visual Studio öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d77b81295ae928fd44c01024e90a873dc79fd3a4
ms.sourcegitcommit: bb1487ef906875ee83f2dc8567bd0bad823d727b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122621756"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Hata ayıklayıcısında Visual Studio ifadeleri
Hata Visual Studio, **QuickWatch** iletişim kutusuna, İzleme penceresine veya Anında görüntü penceresine bir  ifade girebilirsiniz.  İfade değerlendiricileri, Kesme Noktaları penceresinde **ve hata** ayıklayıcıda birçok farklı yerde de çalışır.

Aşağıdaki bölümlerde, bir kullanıcı tarafından desteklenen diller için ifade değerlendirmesinin sınırlamaları Visual Studio.

## <a name="f-expressions-are-not-supported"></a>F# ifadeleri desteklenmiyor
F# ifadeleri tanınmıyor. F# kodunda hata ayıklarsanız, ifadeleri bir hata ayıklayıcısı penceresine veya iletişim kutusuna girmeden önce ifadelerinizi C# söz dizimlerine çevirmeniz gerekir. F# ifadelerini C# diline çevirirken, F# tekini kullanırken C# ile eşitliği test etmek için işleci `==` kullandığından emin `=` olun.

## <a name="c-expressions"></a>C++ İfadeleri
C++ ifadeleriyle bağlam işleçlerini kullanma hakkında bilgi için bkz. [Bağlam İşleci (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>C++'ta Desteklenmeyen İfadeler

#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, yıkıcılar ve dönüştürmeler
Bir nesne için açıkça veya örtülü olarak bir oluşturucu veya yıkıcı çağıramazsiniz. Örneğin, aşağıdaki ifade açıkça bir oluşturucu çağırır ve bir hata iletisiyle sonuç verir:

```C++
my_date( 2, 3, 1985 )
```

Dönüştürmenin hedefi bir sınıfsa dönüştürme işlevini çağıramazsiniz. Bu tür bir dönüştürme, bir nesnenin oluşturma işlemini içerir. Örneğin, dönüştürme işlevi işleci tanımlayan bir örneği `myFraction` `CFraction` `FixedPoint` ise, aşağıdaki ifade bir hatayla sonuç verir:

```C++
(FixedPoint)myFraction
```

Yeni veya silme işleçlerini çağıramazsiniz. Örneğin, aşağıdaki ifade desteklenmiyor:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Önişlemci Makroları
Ön işlemci makroları hata ayıklayıcıda desteklenmiyor. Örneğin, bir sabit `VALUE` şu şekilde bildirildi: `#define VALUE 3` ise, İzleme penceresinde `VALUE` kullanılamaz.  Bu sınırlamayı önlemek için, `#define` 'leri mümkün olduğunca enum'lar ve işlevlerle değiştirmeniz gerekir.

### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma
Bildirimleri `using namespace` kullanılamaz.  Geçerli ad alanının dışındaki bir tür adına veya değişkene erişmek için tam adı kullan gerekir.

### <a name="anonymous-namespaces"></a>Anonim ad alanları
Anonim ad alanları desteklenmiyor. Aşağıdaki koda sahip olursanız, izleme `test` penceresine ekamazsınız:

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
Hata ayıklayıcı iç işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevlerini çağırmanın bir yolunu sağlar.

Hata ayıklayıcısı iç işlevleri:

- Güvenli olması garantidir: bir hata ayıklayıcı iç işlevinin yürütülmesi, hata ayıklama işlemini bozmaz.

- Tüm ifadelerde, yan etkilerin ve işlev değerlendirmesinin izin verilmey olduğu senaryolarda bile izin verilir.

- Mini bir işlevde hata ayıklama gibi normal işlev çağrılarının mümkün olmadığını senaryolarda çalışma.

  Hata ayıklayıcısı iç işlevleri, ifadeleri değerlendirmeyi daha kullanışlı hale de getirir. Örneğin, `strncmp(str, "asd")` bir kesme noktası koşulunda yazmak yerine yazmak çok daha `str[0] == 'a' && str[1] == 's' && str[2] == 'd'` kolaydır. )

|Alan|İç işlevler|
|----------|-------------------------|
|**Dize uzunluğu**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Dize karşılaştırması**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Dize arama**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](/previous-versions/bb432242(v=vs.85)), [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Bu işlevler, hata ayıklama işleminin Windows 8. Bir Windows 8 cihazdan oluşturulan döküm dosyalarında hata ayıklamak için, Visual Studio bilgisayarın Windows 8. Ancak, uzaktan bir Windows 8 hata ayıklarsanız, Visual Studio 7'de Windows çalışıyor olabilir.<br />`WindowsGetStringLen`ve `WindowsGetStringRawBuffer` yalnızca kaynak düzeyinde yürütme altyapısı (EE) tarafından kullanılır.|
|**Çeşitli**|**__log2** - Belirtilen tamsayının 2 günlük tabanını, en yakın alt tamsayıya yuvarlanmış olarak döndürür.<br /><br />**__findNonNull** - İlk null olmayan öğenin dizinini döndürerek bir işaretçi dizisini arar.<br />- Parametreler: (1) Dizideki ilk öğenin işaretçisi (void *), (2) Dizinin boyutu (işaretsiz int). <br /> - Dönüş değerleri: (1) dizideki ilk null olmayan öğenin 0 tabanlı dizini veya bulunamazsa -1. <br /> <br /> **DecodeHString** - HSTRING değerini biçimlendirmek için yardımcı işlevi. HSTRING değerini yığından çıkar, dizenin EE dizenin bulunduğu yeri söylemek için kullanabileceği StringInfo yapısının baytlarını gönderir. Bu yalnızca şirket içinde EE; doğrudan çağrı yapmak kullanıcı tarafından kullanılamaz.<br /><br />**DecodeWinRTRestrictedException** - Kısıtlı açıklamayı almak için WinRT kısıtlanmış özel durum kodunu çöz.<br />- Parametreler: (1) kısıtlanmış başvuru dizesini temsil eden null sonlandırıldı dizenin karakterleri.<br />- Dönüş değeri: Gösterılacak gerçek hata iletisini içeren null olarak sonlandırılan dizenin karakterleri.<br /><br />**DynamicCast** - Uygulama dynamic_cast.<br />- Parametreler: (1) Nesnenin döküme işaretçisi.<br />- Veri öğeleri: CDynamicCastData nesnesi, karşılık gelen ExecuteIntrinsic() yönergesi ile bir veri öğesi olarak ilişkili olması gerekir. Veri öğesi, bir natvis ifadesini değerlendirip değerlendirmemememiz (tanılamanın sonsuz recursion'ı bozması için gereklidir) ve 'den türetilen türü kodlar.<br />- Dönüş değeri: (1) Nesnenin işaretçisi, doğru türe veya türe sahip olan nesne doğru türün bir örneği yoksa NULL.<br /><br />**DynamicMemberLookup** - Bir sınıf üyesinin değerini dinamik olarak almaya yardımcı işlevi<br /><br />**GetEnvBlockLength** - Karakter olarak bir ortam bloğu uzunluğu elde etmek için yardımcı işlevi.  Bu, $env.<br /><br />**Stdext_HashMap_Int_OperatorBracket_idx** - stdext::hash_map için işleç[] .  Varsayılan karma işlevinin 'int' anahtarıyla birlikte olduğunu varsayıyor.  Değerini döndürür. Iç işleci[] yalnızca karma tablosundan mevcut öğelerin alınmasına olanak sağlar. Bu, bellek ayırma gibi istenmeyen karmaşıklıklar da dahil olmak için tabloya yeni öğe ekleme desteğine sahip değildir.  Ancak, işleç[] tabloda zaten bir anahtar ile ilişkili değeri değiştirmek için kullanılabilir.<br />- Yığın Parametreleri: (1) stdext::hash_map nesnesinin adresi, (2) tablonun anahtarı (int), (3) işlev uygulamasının arama yapmak için ihtiyacı olan üyelerin alan uzaklıklarını belirten bir HashMapPdb yapısı.  Sembollere doğrudan erişim uzak tarafta mevcut olduğundan bu gereklidir.<br />- Dönüş değerleri: (1) Anahtar tabloda ise, anahtara karşılık gelen değerin adresi.  Aksi takdirde NULL olur.<br /><br />**Std_UnorderedMap_Int_OperatorBracket_idx** - std::unordered_map, karma işlevi farklı olması dışında stdext::hash_map ile aynı şekilde çalışır.<br /><br />**ConcurrencyArray_OperatorBracket_idx** // Concurrency::array<>::operator[index<>] ve operator(index<>)<br /><br />**ConcurrencyArray_OperatorBracket_int** // Concurrency::array<>::operator(int, int, ...)<br /><br />**ConcurrencyArray_OperatorBracket_tidx** // Concurrency::array<>::operator[tiled_index<>] ve operator(tiled_index<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_idx** // Concurrency::array_view<>::operator[index<>] ve operator(index<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_int** // Concurrency::array_view<>::operator(int, int, ...)<br /><br />**ConcurrencyArrayView_OperatorBracket_tidx** // Concurrency::array_view<>::operator[tiled_index<>] ve operator(tiled_index<>)<br /><br />**TreeTraverse_Init** - Yeni bir ağaç geçişi başlatılır. <br />- Yığın Parametreleri: (1) Kök düğümün adresi, (2) Maksimum derinlik için ipucu.  Bunun ötesindeki öğeler daha sonra iş için kuyruğa taşınır.<br />- Alt yol parametreleri: (1) düğüm geçerliliği (isteğe bağlı).<br />- Dönüş değerleri: (1) Ağaç geçiş durumunu kodlamak için opak bayt dizisi.<br /><br />**TreeTraverse_Next** - Bekleyen bir ağaç geçişten düğümleri alan.<br />- Yığın Parametreleri: (1) Ağaç geçiş durumunu temsil eden opak byte dizisi, (2) Getirilsin düğüm sayısı.<br />- Alt yol parametreleri (TreeTraverse_Init() çağrısıyla eşleşmeli): (1) sol alt, (2) sağ alt, (3) düğüm geçerliliği (isteğe bağlı).<br />- Dönüş değerleri: (1) Getirilmiş düğüm sayısı (Not: düğümlerden sonra kendilerinin, yani ilk olarak alınamalarını sağlar). İstenenden daha az düğüm getirilse, bu ağacın sonu anlamına gelir. (2) Alınan her düğüm için düğümün adresi. (3) Ağaç geçişinin yeni durumunu kodlamak için opak bayt dizisi<br /><br />**TreeTraverse_Skip** -bekleyen bir ağaç geçişinin içindeki düğümleri atlar.<br />-Stack parametreleri: (1) ağaç geçişinin durumunu temsil eden donuk bayt dizisi, (2) atlanacak düğüm sayısı.<br />-Altyordam parametreleri (aynı numaralandırıcı üzerinde sonraki () art arda yapılan çağrılar ile eşleşmelidir): (1) sol alt, (2) sağ alt, (3) düğüm geçerliliği (isteğe bağlı).<br />-Dönüş değerleri: (1) gerçekten atlanan öğe sayısı (istenenden daha az olabilir), (2) ağaç geçişinin yeni durumunu kodlamada donuk bayt dizisi|

## <a name="ccli---unsupported-expressions"></a>C++/CLı-desteklenmeyen Ifadeler

- İşaretçileri veya Kullanıcı tanımlı yayınları içeren yayınlar desteklenmez.

- Nesne karşılaştırma ve atama desteklenmiyor.

- Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmez.

- Kutulama ve kutudan çıkarma desteklenmez.

- `Sizeof` işleç desteklenmiyor.

## <a name="c---unsupported-expressions"></a>C#-desteklenmeyen Ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresi değerlendirildiğinde, dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=` , `-=` ,, `%=` `/=` ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- Boole işleçleri `&&` ve `||`

### <a name="anonymous-methods"></a>Anonim Yöntemler
Yeni anonim yöntemlerin oluşturulması desteklenmez.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic-desteklenmeyen ifadeler

### <a name="dynamic-objects"></a>Dinamik nesneler
Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresi değerlendirildiğinde, dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.

Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:

- Bileşik işleçler `+=` , `-=` ,, `%=` `/=` ve `*=`

- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını

- İkiden fazla bağımsız değişkenle Yöntem çağrıları

- İkiden fazla bağımsız değişkene sahip Özellik alıcıları

- Bağımsız değişkenlerle özellik ayarlayıcıları

- Dizin oluşturucuya atama

- Boole işleçleri `&&` ve `||`

### <a name="local-constants"></a>Yerel sabitler
Yerel sabitler desteklenmez.

### <a name="import-aliases"></a>Diğer adları içeri aktar
İçeri aktarma diğer adları desteklenmez.

### <a name="variable-declarations"></a>Değişken bildirimleri
Hata ayıklayıcı Windows 'da açık yeni değişkenler bildiremezsiniz. Bununla birlikte, **hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumunun kapsamına alınır ve hata ayıklayıcının dışında erişilebilir değildir. Örneğin, ifade `o = 5` örtük olarak yeni bir değişken oluşturur `o` ve 5 değerini bu değere atar. Türü hata ayıklayıcı tarafından çıkarsanmadığı takdirde bu tür örtük değişkenler **Object** türündedir.

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

- Ad alanı veya modül düzeyi anahtar sözcükleri, örneğin `End Sub` veya `Module` .

## <a name="see-also"></a>Ayrıca bkz.
- [C++ içindeki biçim belirticileri](../debugger/format-specifiers-in-cpp.md)
- [Bağlam Işleci (C++)](../debugger/context-operator-cpp.md)
- [C 'de biçim belirticileri #](../debugger/format-specifiers-in-csharp.md)
- [Sözde Değişkenler](../debugger/pseudovariables.md)