---
title: En İyi Yöntemler ve Örnekler (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: ccb18a704c2e8a2c185d3751483736631b0bba68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448638"
---
# <a name="best-practices-and-examples-sal"></a>En İyi Yöntemler ve Örnekler (SAL)
Kaynak kodu ek açıklama dilinden (SAL) en iyi şekilde yararlanmak ve bazı yaygın sorunlardan kaçınmak için bazı yollar aşağıda verilmiştir.

## <a name="_in_"></a>\_In @ no__t-1

İşlevin öğesine yazılması gerekiyorsa, `_In_` yerine `_Inout_` kullanın. Bu özellikle, eski makrolardan SAL 'a otomatik dönüştürme gibi durumlar için geçerlidir. SAL 'dan önce pek çok programcı, makroları açıklama olarak kullanıyordu — `IN`, `OUT`, `IN_OUT` veya bu adların çeşitleri olarak adlandırılan makrolar. Bu makroları SAL 'a dönüştürmenizi öneririz; ancak, özgün prototip yazıldığı ve eski makro artık kodun ne yaptığını yansıtmadığından, bu makroları dönüştürme işlemi için de dikkatli olabilirsiniz. Genellikle yanlış bir şekilde yerleştirildiğinden `OPTIONAL` yorum makrosu hakkında dikkatli olun. Örneğin, bir virgülden sonra yanlış bir kenar üzerinde.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt @ no__t-1

Çağıranın null bir işaretçiye geçmesine izin verilmiyorsa, `_In_opt_` veya `_Out_opt_` yerine `_In_` veya `_Out_` kullanın. Bu, parametrelerini denetleyen ve olmaması gerektiğinde NULL olduğunda bir hata döndüren bir işlev için de geçerlidir. Bir işleve sahip olmak, parametresini beklenmeyen NULL için kontrol edin ve düzgün bir savunma kodlama uygulaması olsa da, parametre ek açıklamanın isteğe bağlı bir tür (`_*Xxx*_opt_`) olabilir.

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre @ no__t-1savunlayıcı @ no__t-2 ve \_Post @ no__t-4savunlayıcı @ no__t-5

Bir işlev güven sınırında görünürse, `_Pre_defensive_` ek açıklamasını kullanmanızı öneririz.  "Savunma" değiştiricisi belirli ek açıklamaları değiştirerek, çağrı noktasında arabirimin kesinlikle denetlenmesi gerektiğini, ancak uygulama gövdesinde yanlış parametrelerin geçirildiğine yönelik olduğunu varsaymalıdır. Bu durumda, `_In_ _Pre_defensive_` ' ı bir güven sınırında tercih edilir, ancak bir arayan, NULL geçirmeye çalışırsa bir hata gerçekleşse de, işlev gövdesi parametre NULL olabilir ve işaretçiye ilk olarak yeniden başvuru yapmaya çalışır. NULL için işaretlemek işaretlenir.  Güvenilen tarafın arayan olarak kabul edildiği ve güvenilmeyen kodun çağrılan kod olduğu geri aramalarda kullanılmak üzere `_Post_defensive_` ek açıklaması da kullanılabilir.

## <a name="_out_writes_"></a>\_Out @ no__t-1yazmaları @ no__t-2

Aşağıdaki örnek `_Out_writes_` ' ın ortak bir kötüye kullanımını gösterir.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

@No__t-0 ek açıklaması, bir arabelleğe sahip olduğunuz anlamına gelir. Çıkış sırasında ilk bayt başlatıldığında `cb` bayt ayrılmış. Bu ek açıklama kesinlikle yanlış değildir ve ayrılan boyutu ifade etmek faydalı olur. Ancak, işlev tarafından kaç öğe başlatıldığını söylemez.

Sonraki örnekte, arabelleğin başlatılmış bölümünün tam boyutunu tam olarak belirtmek için üç doğru yol gösterilmektedir.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_Out @ no__t-1 PSTR

@No__t-0 kullanımı neredeyse her zaman yanlıştır. Bu, bir karakter arabelleğini işaret eden bir çıkış parametresine sahip olarak yorumlanır ve NULL olarak sonlandırılır.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

@No__t-0 gibi bir ek açıklama yaygın ve kullanışlı bir seçenektir. @No__t-0 önkoşulunu NULL ile sonlandırılmış bir dizenin tanınmasını sağladığından, NULL sonlandırmasına sahip bir giriş dizesini işaret eder.

## <a name="_in_-wchar-p"></a>\_In @ no__t-1 WCHAR * p

`_In_ WCHAR* p`, bir karakteri işaret eden bir giriş işaretçisi olduğunu belirtir `p`. Ancak çoğu durumda bu, amaçlanan belirtim olabilir. Bunun yerine, büyük olasılıkla amaçlanan, NULL ile sonlandırılmış bir dizinin belirtimidir; Bunu yapmak için `_In_ PWSTR` ' ı kullanın.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

NULL sonlandırmanın doğru belirtimi eksik. Aşağıdaki örnekte gösterildiği gibi, türü değiştirmek için uygun `STR` sürümünü kullanın.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Out @ no__t-1range @ no__t-2

Parametresi bir işaretçisiyse ve işaretçi tarafından işaret edilen öğe değerinin aralığını ifade etmek istiyorsanız, `_Out_range_` yerine `_Deref_out_range_` kullanın. Aşağıdaki örnekte, * Pcbdoldurulmuş aralığı, Pcbdoldurulmuş değil ifade edilir.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)`, `_Out_writes_to_(cbSize,*pcbFilled)` ' den çıkarsanabileceğinden bazı araçlar için kesinlikle gerekli değildir, ancak bu, tamamlanma açısından burada gösterilmiştir.

## <a name="wrong-context-in-_when_"></a>@No__t-0Olduğunda yanlış bağlam, @ no__t-1

Diğer bir yaygın hata, ön koşullar için durum sonrası değerlendirme kullanmaktır. Aşağıdaki örnekte, `_Requires_lock_held_` bir önkoşuludur.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

@No__t-0 ifadesi, ön durumda kullanılamayan bir durum değeri anlamına gelir.

## <a name="true-in-_success_"></a>@No__t-0Success @ no__t-1 ' de TRUE

Dönüş değeri sıfır olmadığında işlev başarılı olursa, `return == TRUE` yerine başarı koşulu olarak `return != 0` kullanın. Sıfır olmayan değer, derleyicinin `TRUE` için sağladığı gerçek değere eşdeğer bir anlamına gelmez. @No__t-0 ' a yönelik parametre bir ifadedir ve aşağıdaki ifadeler eşdeğer olarak değerlendirilir: `return != 0`, `return != false`, `return != FALSE` ve `return` parametre veya karşılaştırmalar yok.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Başvuru değişkeni

Bir başvuru değişkeni için, SAL 'un önceki sürümü, kapsanan işaretçiyi ek açıklama hedefi olarak kullandı ve bir başvuru değişkenine eklenen ek açıklamaların @no__t 0 ' ın eklenmesini gerektiriyordu. Bu sürüm nesnenin kendisini kullanır ve ek @no__t (0) gerektirmez.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Dönüş değerlerinde ek açıklamalar

Aşağıdaki örnek, dönüş değeri ek açıklamalarıyla ilgili yaygın bir sorunu gösterir.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

Bu örnekte, `_Out_opt_`, işaretçinin önkoşul kapsamında NULL olabileceğini söyler. Ancak, Önkoşullar dönüş değerine uygulanamaz. Bu durumda, doğru ek açıklama `_Ret_maybenull_` ' dır.

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ Kod Hatalarını Azaltmak için SAL Ek Açıklamalarını Kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[SAL'yi Anlama](../code-quality/understanding-sal.md)  
[İşlev Parametrelerini ve Dönüş Değerlerini Açıklama](../code-quality/annotating-function-parameters-and-return-values.md)  
[İşlev Davranışını Yorumlama](../code-quality/annotating-function-behavior.md)  
[Yapıları ve Sınıfları Yorumlama](../code-quality/annotating-structs-and-classes.md)  
[Kilitlenme Davranışını Yorumlama](../code-quality/annotating-locking-behavior.md)  
[Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[İç İşlevler](../code-quality/intrinsic-functions.md)
