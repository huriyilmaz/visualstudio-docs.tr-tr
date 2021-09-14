---
title: Kanca İşlevlerini Ayırma | Microsoft Docs
description: _CrtSetAllocHook'de C çalışma zamanı (CRT) hata ayıklaması yapmak için Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: eada0362b399489bea9bae93863c44e8172abf3c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630986"
---
# <a name="allocation-hook-functions"></a>Atama Kanca İşlevleri
_CrtSetAllocHook kullanılarak yüklenmiş bir [ayırma](/cpp/c-runtime-library/reference/crtsetallochook)kancası işlevi, bellek her serbest bırakıldı, yeniden ayrılır veya serbest bırakıldı. Bu tür kancaları birçok farklı amaçla kullanabilirsiniz. Bir uygulamanın ayırma desenlerini incelemek veya daha sonra analiz etmek üzere günlük ayırma bilgilerini incelemek gibi yetersiz bellek durumlarını nasıl işleyeni test etmek için bunu kullanın.

> [!NOTE]
> Ayırma Kancaları ve C bellek ayırmaları konusunda açıklanan bir ayırma kancası işlevinde C çalışma zamanı [kitaplık işlevlerini kullanma Run-Time farkında olmak.](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)

 Ayırma kancası işlevinin aşağıdaki örnekte olduğu gibi bir prototipi olması gerekir:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Geçiş için geçiş [_CrtSetAllocHook,](/cpp/c-runtime-library/reference/crtsetallochook) CRTDBG'de **_CRT_ALLOC_HOOK** türündedir. H:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Çalışma zamanı kitaplığı kancanızı çağırsa *nAllocType* bağımsız değişkeni hangi ayırma işlemi yapılacak olduğunu **(_HOOK_ALLOC** **,** _HOOK_REALLOC veya **_HOOK_FREE).** Ücretsiz veya yeniden konumlandırmada, `pvData` serbest bırakılana kadar bloğun kullanıcı makalesine bir işaretçisi vardır. Ancak ayırma söz dizimleri söz dizimli olduğundan bu işaretçi null olur. Kalan bağımsız değişkenler söz konusu ayırmanın boyutunu, blok türünü, ilişkili sıralı istek numarasını ve dosya adına yönelik bir işaretçiyi içerir. Varsa, bağımsız değişkenler ayırmanın yapılmış olduğu satır numarasını da içerir. Kanca işlevi, yazarının istediği herhangi bir analizi ve diğer görevleri gerçekleştirdikten sonra, ayırma işleminin devam edeceğini belirten **TRUE**( **veya FALSE)** döndürür ve bu da işleminin başarısız olması gerektiğini gösterir. Bu tür basit bir kanca, o ana kadar ayrılan bellek miktarını kontrol etmek ve bu miktar küçük bir sınırı aşarsa **FALSE** döndürür. Uygulama daha sonra normalde yalnızca kullanılabilir bellek çok düşük olduğunda oluşan ayırma hatalarının türüyle karşılarına çıkabilir. Daha karmaşık kancalar ayırma desenlerini izleyebilir, bellek kullanımını analiz eder veya belirli durumlar oluştuğunda rapor oluşturabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayırma Kancaları ve C Run-Time Ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Kanca İşlevi YazmaDa Hata Ayıklama](../debugger/debug-hook-function-writing.md)