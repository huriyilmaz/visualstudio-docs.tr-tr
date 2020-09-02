---
title: Hata ayıklama kanca Işlevi yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0554c1494bec757d1baecd78cdc302608e5b6b3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573053"
---
# <a name="debug-hook-function-writing"></a>Hata Ayıklama Kanca İşlevi Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, kodunuzu hata ayıklayıcının normal işlemesi içindeki bazı önceden tanımlanmış noktalara eklemenize olanak sağlayan, yazabileceğiniz bir dizi özel hata ayıklama kanca işlevi açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemci Blok Kanca İşlevleri](../debugger/client-block-hook-functions.md)  
 _CLIENT_BLOCK bloklarında depolanan verilerin içeriğini doğrulayan veya rapor eden işlevler yazmak için rehberlik ve prototip sağlar.  
  
 [Atama Kanca İşlevleri](../debugger/allocation-hook-functions.md)  
 Bir ayırma kanca işlevini tanımlar, farklı kullanımlarını araştırır, işaret eden kısıtlamaları gösterir ve bir prototip sağlar.  
  
 [Ayırma kancaları ve CRT bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 `_CRT_BLOCK`İç bellek ayıran C çalışma zamanı kitaplığı işlevlerine çağrılar yaptıysanız blokları açıkça yok saymaya yönelik ayırma kanca işlevleri üzerindeki kısıtlamayı açıklar. Bu konu, ayırma kancaları `_CRT_BLOCK` blokları (örneklerle birlikte) yoksaymayan ve varsayılan ayırma kanca işlevini değiştirme, **CrtDefaultAllocHook**gibi sonuçları da listeler.  
  
 [Kanca İşlevlerini Raporla](../debugger/report-hook-functions.md)  
 `_CrtSetReportHook`Raporları, belirli ayırma türlerine odaklanmak üzere filtrelemek için kullanabileceğiniz açıklanır. Bu konu, bir prototip de sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)  
 CRT hata ayıklama kitaplığı, raporlama için makrolar, ve arasındaki farklar, `malloc` `_malloc_dbg` hata ayıklama kanca IŞLEVLERI ve CRT hata ayıklama yığını gibi C çalışma zamanı kitaplığı için hata ayıklama teknikleri bağlantıları.
