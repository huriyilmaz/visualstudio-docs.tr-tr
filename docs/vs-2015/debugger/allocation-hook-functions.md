---
title: Ayırma kanca Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81135546ffa208a4efb96569cd7968dfe560cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702520"
---
# <a name="allocation-hook-functions"></a>Atama Kanca İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bellek her ayrıldığı, yeniden ayrıldığı veya serbest bırakılmış her seferinde [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)kullanılarak yüklenen bir ayırma kanca işlevi çağırılır. Bu tür bir kanca, birçok farklı amaçla kullanılabilir. Uygulamanın, yetersiz bellek durumlarını nasıl işlediğini test etmek, örneğin, ayırma düzenlerini incelemek veya daha sonra analiz için ayırma bilgilerini günlüğe kaydetmek için kullanın.  
  
> [!NOTE]
> [Ayırma kancaları ve c çalışma zamanı bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)bölümünde açıklanan, bir ayırma kanca işlevinde c çalışma zamanı kitaplık işlevleri kullanma kısıtlamasından haberdar olun.  
  
 Bir ayırma kanca işlevinin, aşağıdaki gibi bir prototipi olmalıdır:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) için geçirdiğiniz işaretçi, CRTDBG içinde tanımlanan **_CRT_ALLOC_HOOK**türündedir. Olsun  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Çalışma zamanı kitaplığı, kancasını çağırdığında, *nAllocType* bağımsız değişkeni hangi ayırma işleminin gerçekleştirildiğini (**_HOOK_ALLOC**, **_HOOK_REALLOC**veya **_HOOK_FREE**) gösterir. Ücretsiz veya yeniden ayırma durumunda, `pvData` serbest bırakmak üzere bloğunun Kullanıcı konusuna yönelik bir işaretçi içerir. Ancak, ayırma durumunda bu işaretçi null olur, çünkü ayırma henüz gerçekleşmemiştir. Kalan bağımsız değişkenler, söz konusu ayırmanın boyutunu, blok türünü, onunla ilişkili ardışık istek numarasını ve varsa, tahsisatın yapıldığı dosya adı ve satır numarası için bir işaretçi içerir. Kanca işlevi, yazarının istediği analiz ve diğer görevleri gerçekleştirdikten sonra, ayırma işleminin devam edebildiğini ya da işlemin başarısız olması gerektiğini belirten **false** **değerini döndürmelidir**. Bu tür bir basit kanca şimdiye kadar ayrılan bellek miktarını denetleyebilir ve bu miktar küçük bir sınırı aşarsa **false** döndürür. Daha sonra uygulama, normalde yalnızca kullanılabilir bellek çok düşük olduğunda oluşacak olan ayırma hatalarının türünü yaşar. Daha karmaşık kancalar, ayırma düzenlerini izleyebilir, bellek kullanımını analiz edebilir veya belirli durumlar gerçekleştiğinde rapor verebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ayırma kancaları ve C çalışma zamanı bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 örneği](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
