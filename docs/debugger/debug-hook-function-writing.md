---
title: Hata Ayıklama Kanca İşlevi Yazma | Microsoft Docs
description: Kodunuzu hata ayıklayıcının normal işlemesi içindeki önceden tanımlanmış noktalara eklemenizi sağlarken yazabilirsiniz bir dizi özel hata ayıklama kancası işlevi hakkında bilgi alın.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fb99734182a2a5c218cdabaff6f219d3918245c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630788"
---
# <a name="debug-hook-function-writing"></a>Hata Ayıklama Kanca İşlevi Yazma
Bu bölümde, kodunuzu hata ayıklayıcının normal işlemesinde önceden tanımlanmış bazı noktalara eklemenizi sağlayan yazabilir bir dizi özel hata ayıklama kancası işlevi açıkmektedir.

## <a name="in-this-section"></a>Bu Bölümde
 [İstemci Bloğu Kanca İşlevleri](../debugger/client-block-hook-functions.md) Bloklarda depolanan verilerin içeriğini doğrulayan veya raporlayan işlevler yazmaya yönelik rehberlik ve _CLIENT_BLOCK sağlar.

 [Kanca İşlevlerini Ayırma](../debugger/allocation-hook-functions.md) Ayırma kancası işlevini tanımlar, farklı kullanımlarını keşfeder, kısıtlamaları gösterir ve bir prototip sağlar.

 [Atama Kancaları ve CRT Bellek Ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) İç bellek ayıran C çalışma zamanı kitaplık işlevlerine çağrı yapmaları durumda blokları açıkça yoksayarak ayırma kanca işlevleri `_CRT_BLOCK` kısıtlamasını açıklar. Bu konuda ayrıca, ayırma kancanız blokları yoksaymasa (örneklerle birlikte) ve varsayılan ayırma kancası işlevinin `_CRT_BLOCK` **(CrtDefaultAllocHook)** nasıl değiştirilemeyecekleri de listelemektedir.

 [Rapor Kancası İşlevleri](../debugger/report-hook-functions.md) Belirli `_CrtSetReportHook` ayırma türlerine odaklanmak üzere raporları filtrelemek için kullanabileceğiniz konusunu ele alır. Bu konu ayrıca bir prototip sağlar.

## <a name="related-sections"></a>İlgili Bölümler

- [CRT Hata Ayıklama](../debugger/crt-debugging-techniques.md) Teknikleri - CRT Hata Ayıklama Kitaplığı'nın kullanımı, raporlama makroları, ile arasındaki farklar, hata ayıklama kancası işlevleri yazma ve CRT hata ayıklama yığını dahil olmak üzere C Run-Time Kitaplığı için hata ayıklama tekniklerine `malloc` `_malloc_dbg` bağlantılar.