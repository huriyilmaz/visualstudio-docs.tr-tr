---
title: Yığın ayırma Işlevlerinin hata ayıklama sürümleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738367"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Öbek Atama İşlevleri Hata Ayıklama Sürümleri
C çalışma zamanı kitaplığı, yığın ayırma işlevlerinin özel hata ayıklama sürümlerini içerir. Bu işlevler, _dbg öğesine eklenen sürüm sürümleriyle aynı ada sahiptir. Bu konu, örnek olarak `malloc` ve `_malloc_dbg` kullanarak bir CRT işlevinin yayın sürümü ve _dbg sürümü arasındaki farkları açıklamaktadır.

 [_Hata ayıklama](/cpp/c-runtime-library/debug) TANıMLANDıĞıNDA, CRT tüm [malloc](/cpp/c-runtime-library/reference/malloc) çağrılarını [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)öğesine eşler. Bu nedenle, hata ayıklarken avantajları almak için `malloc` yerine `_malloc_dbg` kullanarak kodunuzu yeniden yazmanız gerekmez.

 Ancak `_malloc_dbg` açıkça çağırmak isteyebilirsiniz. @No__t_0 açıkça çağırmak bazı ek avantajlara sahiptir:

- @No__t_0 türü ayırmaları izleniyor.

- Kaynak dosya ve ayırma isteğinin gerçekleştiği satır numarası depolanıyor.

  @No__t_0 çağrılarınızı `_malloc_dbg` dönüştürmek istemiyorsanız, [_Crtdbg_map_poal](/cpp/c-runtime-library/crtdbg-map-alloc)' ı tanımlayarak kaynak dosya bilgilerini elde edebilirsiniz. Bu, Önişlemci 'nin bir sarmalayıcı temelinde `malloc` tüm çağrıları doğrudan `_malloc_dbg` 'e eşlemesine neden olur.  `malloc`.

  İstemci bloklarında ayrı ayırma türlerini izlemek için `_malloc_dbg` doğrudan çağırmanız ve `blockType` parametresini `_CLIENT_BLOCK` olarak ayarlamanız gerekir.

  _HATA ayıklama tanımlanmadığında, `malloc` çağrıları olumsuz olmaz, `_malloc_dbg` çağrıları `malloc` olarak çözümlenir, [_Crtdbg_map_allocation](/cpp/c-runtime-library/crtdbg-map-alloc) tanımı yok sayılır ve ayırma isteğiyle ilgili kaynak dosya bilgileri sağlanmaz. @No__t_0 bir blok türü parametresine sahip olmadığından, `_CLIENT_BLOCK` türleri için istekler standart ayırma olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.

- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)