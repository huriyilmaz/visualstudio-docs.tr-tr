---
title: Ayırma kancaları ve C çalışma zamanı bellek ayırmaları | Microsoft Docs
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702431"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayırma kanca işlevleriyle ilgili çok önemli bir kısıtlama, `_CRT_BLOCK` iç bellek ayıran c çalışma zamanı kitaplığı işlevlerine çağrılar yaparsanız blokları (c çalışma zamanı kitaplığı işlevleri tarafından dahili olarak yapılan bellek ayırmaları) açıkça yoksaymalıdır. `_CRT_BLOCK`Bloklar, ayırma kanca işlevinizin başlangıcında aşağıdakiler gibi kod ekleyerek yoksayılabilir:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Ayırma kanca blokları yok saymaz `_CRT_BLOCK` , kanca içinde çağrılan tüm C çalışma zamanı kitaplığı işlevleri programı sonsuz bir döngüde yakalayabilir. Örneğin, `printf` bir iç ayırma yapar. Kanca kodunuz `printf` çağrılırsa, elde edilen ayırma, kancalarınızın yeniden çağrılmasına neden olur, bu da **printf** 'i yeniden çağırır ve yığın taşana kadar bu şekilde devam eder. Ayırma işlemlerini rapor etmeniz gerekiyorsa `_CRT_BLOCK` , bu kısıtlamayı aşmak için bir yol, biçimlendirme ve çıkış Için C çalışma zamanı işlevleri yerine WINDOWS API işlevlerini kullanmaktır. Windows API 'Leri C çalışma zamanı kitaplık yığınını kullanmadığından, ayırma Kancalarınızı sonsuz bir döngüde yakalamaz.  
  
 Çalışma zamanı kitaplık kaynak dosyalarını incelerseniz, varsayılan ayırma kanca işlevinin **CrtDefaultAllocHook** (basitçe **doğru**döndüren), kendi kendine ait ayrı bir dosyada bulunduğunu görürsünüz. Uygulamanızın **ana** işlevinden önce yürütülen çalışma zamanı başlangıç kodu tarafından yapılan ayırmalar için bile ayırma kancasını çağırmasını istiyorsanız, [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)kullanmak yerine, bu varsayılan işlevi kendi sahip olduğunuz bir biriyle değiştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 örneği](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
