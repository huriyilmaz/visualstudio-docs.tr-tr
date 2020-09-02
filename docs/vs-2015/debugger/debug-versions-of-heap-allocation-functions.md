---
title: Yığın ayırma Işlevlerinin hata ayıklama sürümleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691167"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Öbek Atama İşlevleri Hata Ayıklama Sürümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C çalışma zamanı kitaplığı, yığın ayırma işlevlerinin özel hata ayıklama sürümlerini içerir. Bu işlevler, _dbg eklenen sürüm sürümleriyle aynı ada sahiptir. Bu konu, bir CRT işlevinin yayın sürümü ve _dbg sürümü arasındaki farkları `malloc` ve örnekleri kullanılarak açıklar `_malloc_dbg` .  
  
 [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) TANıMLANDıĞıNDA, CRT tüm [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) çağrılarını [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)eşler. Bu nedenle, `_malloc_dbg` `malloc` hata ayıklarken avantajları almak için yerine kodunuzu yeniden yazmanız gerekmez.  
  
 `_malloc_dbg`Ancak, açıkça çağırmak isteyebilirsiniz. `_malloc_dbg`Açıkça çağırmak bazı ek avantajlara sahiptir:  
  
- `_CLIENT_BLOCK`Tür ayırmaları izleniyor.  
  
- Kaynak dosya ve ayırma isteğinin gerçekleştiği satır numarası depolanıyor.  
  
  Çağrılarınızı öğesine dönüştürmek istemiyorsanız, Önişlemci 'nin `malloc` `_malloc_dbg` [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) `malloc` `_malloc_dbg` çevresindeki bir sarmalayıcı temelinde tüm çağrıları öğesine doğrudan eşlemesine neden olan _CRTDBG_MAP_ALLOC tanımlayarak kaynak dosya bilgilerini elde edebilirsiniz `malloc` .  
  
  İstemci bloklarında ayrı ayırma türlerini izlemek için, `_malloc_dbg` doğrudan çağırmanız ve `blockType` parametresini olarak ayarlamanız gerekir `_CLIENT_BLOCK` .  
  
  _DEBUG tanımlanmadığında, çağrısı olumsuz değildir, öğesine yapılan `malloc` çağrılar `_malloc_dbg` olarak çözümlenir `malloc` , [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) tanımı yok sayılır ve ayırma isteğiyle ilgili kaynak dosya bilgileri sağlanmaz. `malloc`Bir blok türü parametresine sahip olmadığından, `_CLIENT_BLOCK` türlerin istekleri Standart ayırma olarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
