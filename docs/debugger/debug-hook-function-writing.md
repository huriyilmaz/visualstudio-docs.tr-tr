---
title: Hata ayıklama kanca Işlevi yazma | Microsoft Docs
description: Kodunuzu hata ayıklayıcının normal işlemesi içinde önceden tanımlanmış noktalara eklemenizi sağlamak için yazabilen özel hata ayıklama kancası işlevleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76727da1ed057902d8f757594f5ed2e07bcf3cea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857551"
---
# <a name="debug-hook-function-writing"></a>Hata Ayıklama Kanca İşlevi Yazma
Bu bölümde, kodunuzu hata ayıklayıcının normal işlemesi içindeki bazı önceden tanımlanmış noktalara eklemenize olanak sağlayan, yazabileceğiniz bir dizi özel hata ayıklama kanca işlevi açıklanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
 [Istemci blok kanca işlevleri](../debugger/client-block-hook-functions.md) _CLIENT_BLOCK bloklarında depolanan verilerin içeriğini doğrulayan veya rapor eden işlevler yazmak için rehberlik ve prototip sağlar.

 [Ayırma kanca işlevleri](../debugger/allocation-hook-functions.md) Bir ayırma kanca işlevini tanımlar, farklı kullanımlarını araştırır, işaret eden kısıtlamaları gösterir ve bir prototip sağlar.

 [Ayırma kancaları ve crt bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) `_CRT_BLOCK` İç bellek ayıran C çalışma zamanı kitaplığı işlevlerine çağrılar yaptıysanız blokları açıkça yok saymaya yönelik ayırma kanca işlevleri üzerindeki kısıtlamayı açıklar. Bu konu, ayırma kancaları `_CRT_BLOCK` blokları (örneklerle birlikte) yoksaymayan ve varsayılan ayırma kanca işlevini değiştirme, **CrtDefaultAllocHook** gibi sonuçları da listeler.

 [Rapor kancası işlevleri](../debugger/report-hook-functions.md) `_CrtSetReportHook`Raporları, belirli ayırma türlerine odaklanmak üzere filtrelemek için kullanabileceğiniz açıklanır. Bu konu, bir prototip de sağlar.

## <a name="related-sections"></a>İlgili Bölümler

- [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md) -CRT hata ayıklama kitaplığı, raporlama için makrolar, ve arasındaki farklar, `malloc` `_malloc_dbg` hata ayıklama kanca işlevleri ve CRT hata ayıklama yığını gibi, C Run-Time kitaplığı için hata ayıklama teknikleri bağlantıları.