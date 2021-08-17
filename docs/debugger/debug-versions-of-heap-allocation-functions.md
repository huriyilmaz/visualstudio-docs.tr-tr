---
title: Yığın ayırma Işlevlerinin hata ayıklama sürümleri | Microsoft Docs
description: C çalışma zamanı kitaplığındaki yığın ayırma işlevlerinin hata ayıklama sürümlerini kullanın. Bu işlevler, _dbg eklenen sürüm sürümleriyle aynı ada sahiptir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 47a704d69fb0a3487deaf14962a65d0b04fe00ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105394"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Öbek Atama İşlevleri Hata Ayıklama Sürümleri
C çalışma zamanı kitaplığı, yığın ayırma işlevlerinin özel hata ayıklama sürümlerini içerir. Bu işlevler, _dbg eklenen sürüm sürümleriyle aynı ada sahiptir. Bu konu, bir CRT işlevinin yayın sürümü ve _dbg sürümü arasındaki farkları `malloc` ve örnekleri kullanılarak açıklar `_malloc_dbg` .

 [_DEBUG](/cpp/c-runtime-library/debug) TANıMLANDıĞıNDA, CRT tüm [malloc](/cpp/c-runtime-library/reference/malloc) çağrılarını [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)eşler. Bu nedenle, `_malloc_dbg` `malloc` hata ayıklarken avantajları almak için yerine kodunuzu yeniden yazmanız gerekmez.

 `_malloc_dbg`Ancak, açıkça çağırmak isteyebilirsiniz. `_malloc_dbg`Açıkça çağırmak bazı ek avantajlara sahiptir:

- `_CLIENT_BLOCK`Tür ayırmaları izleniyor.

- Kaynak dosya ve ayırma isteğinin gerçekleştiği satır numarası depolanıyor.

  Çağrılarınızı öğesine dönüştürmek istemiyorsanız, Önişlemci 'nin `malloc` `_malloc_dbg` [](/cpp/c-runtime-library/crtdbg-map-alloc) `malloc` `_malloc_dbg` çevresindeki bir sarmalayıcı temelinde tüm çağrıları öğesine doğrudan eşlemesine neden olan _CRTDBG_MAP_ALLOC tanımlayarak kaynak dosya bilgilerini elde edebilirsiniz `malloc` .

  İstemci bloklarında ayrı ayırma türlerini izlemek için, `_malloc_dbg` doğrudan çağırmanız ve `blockType` parametresini olarak ayarlamanız gerekir `_CLIENT_BLOCK` .

  _DEBUG tanımlanmadığında, çağrısı olumsuz değildir, öğesine yapılan `malloc` çağrılar `_malloc_dbg` olarak çözümlenir `malloc` , [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) tanımı yok sayılır ve ayırma isteğiyle ilgili kaynak dosya bilgileri sağlanmaz. `malloc`Bir blok türü parametresine sahip olmadığından, `_CLIENT_BLOCK` türlerin istekleri Standart ayırma olarak değerlendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)