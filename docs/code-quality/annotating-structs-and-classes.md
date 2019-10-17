---
title: Yapıları ve Sınıfları Yorumlama
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: ac3d6225bc765ec404784589d2faa06f155265ab
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446290"
---
# <a name="annotating-structs-and-classes"></a>Yapıları ve Sınıfları Yorumlama

Struct ve Class üyelerine, ınvarıant gibi davranan ek açıklamaları kullanarak açıklama ekleyebilirsiniz — bir parametre çağrısı veya bir sonuç değeri olarak kapsayan yapıyı içeren herhangi bir işlev çağrısında ya da işlev girişinde/çıkışta doğru olarak kabul edilir.

## <a name="struct-and-class-annotations"></a>Struct ve sınıf ek açıklamaları

- `_Field_range_(low, high)`

     Alan, `low` ile `high` arasında (dahil) aralığıdır.  İlgili ön veya gönderi koşulları kullanılarak açıklamalı nesneye uygulanan `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` ' a eşdeğerdir.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     @No__t-0 ile belirtilen öğeler (veya bayt) içinde yazılabilir boyutu olan bir alan.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     @No__t-0 tarafından belirtilen öğeler (veya bayt) ve okunabilir olan bu öğelerin (bayt) `count` ' de, yazılabilir boyutu olan bir alan.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     @No__t-0 tarafından belirtilen öğelerde (veya baytların) hem okunabilir hem de yazılabilir boyuta sahip bir alan.

- `_Field_z_`

     Null ile sonlandırılmış bir dizeye sahip alan.

- `_Struct_size_bytes_(size)`

     Struct veya Class bildirimi için geçerlidir.  Bu türdeki geçerli bir nesnenin, `size` tarafından belirtilen bayt sayısıyla, belirtilen tür ile daha büyük olabileceğini gösterir.  Örneğin:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     @No__t-1 türündeki `pM` parametresinin bayt cinsinden arabellek boyutu şu şekilde yapılır:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Örnek

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

Bu örneğe ilişkin notlar:

- `_Field_z_` `_Null_terminated_` ' e eşdeğerdir.  ad alanı için `_Field_z_`, ad alanının null ile sonlandırılmış bir dize olduğunu belirtir.
- `bufferSize` için `_Field_range_` `bufferSize` değerinin 1 ile `MaxBufferSize` (her ikisi de dahil) arasında olması gerektiğini belirtir.
- @No__t-0 ve `_Field_size_` ek açıklamaların nihai sonuçları eşdeğerdir. Benzer düzeni olan yapılar veya sınıflar için `_Field_size_` ' ı okumak ve sürdürmek daha kolaydır, çünkü eşdeğer `_Struct_size_bytes_` ek açıklamasına göre daha az başvuru ve hesaplamalar vardır. `_Field_size_` ' ın bayt boyutuna dönüştürülmesi gerekmez. Bayt boyutu tek seçenektir, örneğin, void işaretçi alanı için `_Field_size_bytes_` kullanılabilir. Hem `_Struct_size_bytes_` hem de `_Field_size_` varsa, her ikisi de araçlar tarafından kullanılabilir. Bu, iki ek açıklama kabul eterif durumunda ne yapmanız gerektiğini araca kadar olur.

## <a name="see-also"></a>Ayrıca Bkz.

- [C/C++ Kod Hatalarını Azaltmak için SAL Ek Açıklamalarını Kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL'yi Anlama](../code-quality/understanding-sal.md)
- [İşlev Parametrelerini ve Dönüş Değerlerini Açıklama](../code-quality/annotating-function-parameters-and-return-values.md)
- [İşlev Davranışını Yorumlama](../code-quality/annotating-function-behavior.md)
- [Kilitlenme Davranışını Yorumlama](../code-quality/annotating-locking-behavior.md)
- [Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [İç İşlevler](../code-quality/intrinsic-functions.md)
- [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
