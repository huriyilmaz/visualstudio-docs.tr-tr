---
title: İstemci blok kanca Işlevleri | Microsoft Docs
description: _CLIENT_BLOCK bloklarında depolanan verilerin içeriğini doğrulamak veya raporlamak için bir istemci blok kanca işlevi yazın.
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
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0378f2260a9bf71cf7ac1192b7eb7a2259d8ace2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865884"
---
# <a name="client-block-hook-functions"></a>İstemci Blok Kanca İşlevleri
Bloklar halinde depolanan verilerin içeriğini doğrulamak veya raporlamak isterseniz `_CLIENT_BLOCK` , bu amaçla özel olarak bir işlev yazabilirsiniz. Yazdığınız işlev, CRTDBG içinde tanımlandığı şekilde aşağıdakine benzer bir prototipi içermelidir. Olsun

```cpp
void YourClientDump(void *, size_t)
```

 Diğer bir deyişle, kanca işleviniz, ayırma bloğunun başlangıcına, ayırma boyutunu belirten bir **size_t** tür değeriyle birlikte bir **void** işaretçisi kabul etmelidir ve döndürülür `void` . Bunun dışında, içeriği size ait.

 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanarak kanca işlevinizi yükledikten sonra, bir `_CLIENT_BLOCK` blok her döküşinizde çağrılacaktır. Daha sonra, dökübir blok türü veya alt türü hakkında bilgi almak için [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) kullanabilirsiniz.

 İşlevinizin geçirdiğiniz işaretçi, `_CrtSetDumpClient` CRTDBG içinde tanımlandığı gibi **_CRT_DUMP_CLIENT** türündedir. Olsun

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 örneği](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)