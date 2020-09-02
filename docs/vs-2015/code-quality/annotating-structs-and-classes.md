---
title: Yapı ve sınıflara açıklama ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271575"
---
# <a name="annotating-structs-and-classes"></a>Yapıları ve Sınıfları Yorumlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Struct ve Class üyelerine, ınvarıant gibi davranan ek açıklamaları kullanarak açıklama ekleyebilirsiniz — bir parametre çağrısı veya bir sonuç değeri olarak kapsayan yapıyı içeren herhangi bir işlev çağrısında ya da işlev girişinde/çıkışta doğru olarak kabul edilir.  
  
## <a name="struct-and-class-annotations"></a>Struct ve sınıf ek açıklamaları  
  
- `_Field_range_(low, high)`  
  
     Alan, ile arasında (dahil) aralığıdır `low` `high` .  `_Satisfies_(_Curr_ >= low && _Curr_ <= high)`İlgili ön koşul veya gönderi koşulları kullanılarak açıklamalı nesneye uygulanan eşdeğerdir.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Öğesinde belirtilen öğeler (veya bayt) içinde yazılabilir boyutu olan bir alan `size` .  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Tarafından belirtilen öğeler (veya bayt) `size` ve `count` okunabilir olan öğelerin (bayt) içinde yazılabilir boyutu olan bir alan.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Öğesinde belirtilen öğeler (veya bayt) içinde hem okunabilir hem de yazılabilir boyuta sahip bir alan `size` .  
  
- `_Struct_size_bytes_(size)`  
  
     Öğesinde belirtilen öğeler (veya bayt) içinde hem okunabilir hem de yazılabilir boyuta sahip bir alan `size` .  
  
     Struct veya Class bildirimi için geçerlidir.  Bu türdeki geçerli bir nesnenin, tarafından belirtilen bayt sayısıyla, belirtilen tür ile daha büyük olabileceğini gösterir `size` .  Örneğin:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Daha sonra, türündeki bir parametrenin bayt cinsinden arabellek boyutu `pM` `MyStruct *` Şu şekilde alınır:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 'ı anlama](../code-quality/understanding-sal.md)   
 [Işlev parametrelerine ve dönüş değerlerine açıklama ekleme](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md)   
 [Kilitleme davranışına açıklama ekleme](../code-quality/annotating-locking-behavior.md)   
 [Ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç Işlevler](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
