---
title: Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
description: Visual Studio Hata ayıklamasında ayırma kancalarını ve C çalışma zamanı bellek ayırmalarını anlayın. Ayırma kanca işlevleri _CRT_BLOCK blokları açıkça yoksaymalıdır.
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
ms.openlocfilehash: f2c9225281952700b118f13b20a11f7619307b8e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729177"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
Ayırma kanca işlevlerinde çok önemli bir kısıtlama, blokları açıkça yoksaymalıdır `_CRT_BLOCK` . Bu bloklar, iç bellek ayıran C çalışma zamanı kitaplığı işlevlerine çağrılar yaptıklarında C çalışma zamanı kitaplığı işlevleri tarafından dahili olarak oluşturulan bellek ayırmaların bir süredir. `_CRT_BLOCK`Ayırma kanca işlevinizin başlangıcında aşağıdaki kodu ekleyerek blokları yoksayabilirsiniz:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Ayırma kanca blokları yok saymazsa `_CRT_BLOCK` , kanca içinde çağrılan tüm C çalışma zamanı kitaplığı işlevleri programı sonsuz bir döngüde yakalayabilir. Örneğin, `printf` bir iç ayırma yapar. Kanca kodunuz `printf` çağrılırsa, sonuçta elde edilen ayırma, aramalarınızın yeniden çağrılmasına neden olur; bu da, yığın taşana kadar **printf** 'i yeniden çağırır ve bu şekilde devam eder. Ayırma işlemlerini rapor etmeniz gerekiyorsa `_CRT_BLOCK` , bu kısıtlamayı aşmak için bir yol, biçimlendirme ve çıkış Için C çalışma zamanı işlevleri yerine WINDOWS API işlevlerini kullanmaktır. Windows API 'Leri C çalışma zamanı kitaplık yığınını kullanmadığından, ayırma kancasını sonsuz bir döngüde yakalamaz.

Çalışma zamanı kitaplık kaynak dosyalarını incelerseniz, varsayılan ayırma kanca işlevinin **CrtDefaultAllocHook** (basitçe **doğru** döndüren), kendi kendine ait ayrı bir dosyada bulunduğunu görürsünüz. Uygulamanızın **ana** işlevinden önce yürütülen çalışma zamanı başlangıç kodu tarafından yapılan ayırmalar için bile ayırma kancasını çağırmasını istiyorsanız, [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)kullanmak yerine, bu varsayılan işlevi kendi sahip olduğunuz bir biriyle değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)
