---
title: Yığın Ayırma İşlevlerinin Hata Ayıklama Sürümleri | Microsoft Docs
description: C çalışma zamanı kitaplığında yığın ayırma işlevlerinin hata ayıklama sürümlerini kullanın. Bu işlevler, yayın sürümleriyle aynı adlara sahiptir ve _dbg eklenir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 12a81eb56b968c1b2a07f0accdf6ef58b192f3f0
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805318"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Öbek Atama İşlevleri Hata Ayıklama Sürümleri
C çalışma zamanı kitaplığı, yığın ayırma işlevlerinin özel Hata Ayıklama sürümlerini içerir. Bu işlevler, yayın sürümleriyle aynı adlara ve _dbg sahiptir. Bu konuda, örnek olarak ve kullanarak bir CRT işlevinin Yayın sürümü ile _dbg sürümü arasındaki `malloc` `_malloc_dbg` farklar açıklanmıştır.

 Bu [_DEBUG](/cpp/c-runtime-library/debug) tanımlandığı zaman, CRT tüm [yanlış konum çağrılarını](/cpp/c-runtime-library/reference/malloc) _malloc_dbg. [](/cpp/c-runtime-library/reference/malloc-dbg) Bu nedenle, hata ayıklama sırasında avantajları almak yerine kullanarak `_malloc_dbg` `malloc` kodunuzu yeniden yazmanız gerekli değildir.

 Ancak, açıkça `_malloc_dbg` çağrısı yapmak istiyor olabilir. Açıkça `_malloc_dbg` çağırmanın bazı avantajları vardır:

- Tür `_CLIENT_BLOCK` ayırmalarını izleme.

- Ayırma isteğinin meydana geldiği kaynak dosyayı ve satır numarasını depolama.

  Çağrılarınızı 'a dönüştürmek `malloc` istemiyorsanız, _CRTDBG_MAP_ALLOC'i tanımlayarak kaynak dosya bilgilerini edinebilirsiniz. Bu da ön işlemcinin çevresindeki bir sarmalayıcıya güvenmek yerine tüm çağrıları doğrudan ile eşlemesine `_malloc_dbg` [](/cpp/c-runtime-library/crtdbg-map-alloc) `malloc` neden `_malloc_dbg` `malloc` olur.

  İstemci bloklarında ayrı ayırma türlerini izlemek için doğrudan çağırmalı ve `_malloc_dbg` parametresini olarak `blockType` ayarlayabilirsiniz. `_CLIENT_BLOCK`

  Bu _DEBUG, çağrıları rahatsız edilmez, çağrıları ile çözümlenir, _CRTDBG_MAP_ALLOC tanımı yoksayılır ve ayırma isteğiyle ilgili kaynak dosya `malloc` `_malloc_dbg` bilgileri `malloc` sağlanmaz. [](/cpp/c-runtime-library/crtdbg-map-alloc) Blok `malloc` türü parametresine sahip olmayan türlere ilişkin `_CLIENT_BLOCK` istekler standart ayırma olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.

- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)