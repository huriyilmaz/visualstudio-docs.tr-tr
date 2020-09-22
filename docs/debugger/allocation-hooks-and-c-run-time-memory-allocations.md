---
title: Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be75b4d3e83ed297f31e9015c7ba082c0611206d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851625"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
Ayırma kanca işlevlerinde çok önemli bir kısıtlama, blokları açıkça yoksaymalıdır `_CRT_BLOCK` . Bu bloklar, iç bellek ayıran C çalışma zamanı kitaplığı işlevlerine çağrılar yaptıklarında C çalışma zamanı kitaplığı işlevleri tarafından dahili olarak oluşturulan bellek ayırmaların bir süredir. `_CRT_BLOCK`Ayırma kanca işlevinizin başlangıcında aşağıdaki kodu ekleyerek blokları yoksayabilirsiniz:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Ayırma kanca blokları yok saymazsa `_CRT_BLOCK` , kanca içinde çağrılan tüm C çalışma zamanı kitaplığı işlevleri programı sonsuz bir döngüde yakalayabilir. Örneğin, `printf` bir iç ayırma yapar. Kanca kodunuz `printf` çağrılırsa, sonuçta elde edilen ayırma, aramalarınızın yeniden çağrılmasına neden olur; bu da, yığın taşana kadar **printf** 'i yeniden çağırır ve bu şekilde devam eder. Ayırma işlemlerini rapor etmeniz gerekiyorsa `_CRT_BLOCK` , bu kısıtlamayı aşmak için bir yol, biçimlendirme ve çıkış Için C çalışma zamanı işlevleri yerine WINDOWS API işlevlerini kullanmaktır. Windows API 'Leri C çalışma zamanı kitaplık yığınını kullanmadığından, ayırma kancasını sonsuz bir döngüde yakalamaz.

Çalışma zamanı kitaplık kaynak dosyalarını incelerseniz, varsayılan ayırma kanca işlevinin **CrtDefaultAllocHook** (basitçe **doğru**döndüren), kendi kendine ait ayrı bir dosyada bulunduğunu görürsünüz. Uygulamanızın **ana** işlevinden önce yürütülen çalışma zamanı başlangıç kodu tarafından yapılan ayırmalar için bile ayırma kancasını çağırmasını istiyorsanız, [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)kullanmak yerine, bu varsayılan işlevi kendi sahip olduğunuz bir biriyle değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)
