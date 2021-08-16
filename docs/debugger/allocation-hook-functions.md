---
title: Ayırma kanca Işlevleri | Microsoft Docs
description: Visual Studio ' de C çalışma zamanı (CRT) hata ayıklaması yapmanız gerektiğinde _CrtSetAllocHook kullanılarak yüklenen ayırma kanca işlevlerini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 5406cf76eee3ae81ea629e2bc41b4d97cb7d68cdae5e4f9cb48a43b24547fc6e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346381"
---
# <a name="allocation-hook-functions"></a>Atama Kanca İşlevleri
Bellek her ayrıldığı, yeniden ayrıldığı veya serbest bırakılmış her seferinde [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)kullanılarak yüklenen bir ayırma kanca işlevi çağırılır. Bu tür bir kanca, birçok farklı amaçla kullanabilirsiniz. Uygulamanın, ayırma düzenlerini incelemek veya daha sonra analiz edilmek üzere günlük ayırma bilgileri gibi yetersiz bellek durumlarını nasıl işlediğini sınamak için kullanın.

> [!NOTE]
> [Ayırma kancaları ve c Run-Time bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)bölümünde açıklanan bir ayırma kanca işlevinde c çalışma zamanı kitaplık işlevleri kullanma kısıtlamasından haberdar olun.

 Bir ayırma kanca işlevinin aşağıdaki örnekte olduğu gibi bir prototipi olmalıdır:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) için geçirdiğiniz işaretçi, CRTDBG içinde tanımlanan **_CRT_ALLOC_HOOK** türündedir. Olsun

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Çalışma zamanı kitaplığı, kancasını çağırdığında, *nAllocType* bağımsız değişkeni hangi ayırma işleminin yapılması gerektiğini (**_HOOK_ALLOC**, **_HOOK_REALLOC** veya **_HOOK_FREE**) gösterir. Ücretsiz veya yeniden tahsisatın içinde, `pvData` bloonun serbest bırakmak için Kullanıcı makalesinin bir işaretçisi vardır. Ancak, ayırma gerçekleşmediği için bu işaretçi null olur. Kalan bağımsız değişkenler söz konusu ayırmanın boyutunu, blok türünü, onunla ilişkili ardışık istek numarasını ve dosya adı işaretçisini içerir. Varsa, bağımsız değişkenler ayırmanın yapıldığı satır numarasını da içerir. Kanca işlevi, yazarının istediği analiz ve diğer görevleri gerçekleştirdikten sonra, ayırma işleminin devam edebildiğini ya da işlemin başarısız olması gerektiğini belirten **false** **değerini döndürmelidir**. Bu tür bir basit kanca şimdiye kadar ayrılan bellek miktarını denetleyebilir ve bu miktar küçük bir sınırı aşarsa **false** döndürür. Daha sonra uygulama, normalde yalnızca kullanılabilir bellek çok düşük olduğunda oluşacak olan ayırma hatalarının türünü yaşar. Daha karmaşık kancalar, ayırma düzenlerini izleyebilir, bellek kullanımını analiz edebilir veya belirli durumlar gerçekleştiğinde rapor verebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayırma kancaları ve C Run-Time bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)