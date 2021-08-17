---
title: İstemci Blok Kancası İşlevleri | Microsoft Docs
description: Bloklarda depolanan verilerin içeriğini doğrulamak veya rapor etmek için bir istemci bloğu kanca _CLIENT_BLOCK yazın.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3528d52f7e185c804d2f56b3cc9b0baa61228f38
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066906"
---
# <a name="client-block-hook-functions"></a>İstemci Blok Kanca İşlevleri
Bloklarda depolanan verilerin içeriğini doğrulamak veya rapor etmek için `_CLIENT_BLOCK` özel olarak bu amaca yönelik bir işlev yazabilirsiniz. CRTDBG'de tanımlandığı gibi, yazacak işlevin aşağıdakine benzer bir prototipi olması gerekir. H:

```cpp
void YourClientDump(void *, size_t)
```

 Başka bir deyişle, kanca işleviniz ayırma bloğun başına bir void  işaretçisi kabul size_t ayırmanın boyutunu belirten bir tür değeriyle birlikte ve değerini geri  `void` getirerek. Bunun dışında içeriği size göredir.

 _CrtSetDumpClient kullanarak kanca işlevinizi [yüklemiş](/cpp/c-runtime-library/reference/crtsetdumpclient)olduktan sonra, bir blok her `_CLIENT_BLOCK` atılmışken çağrılır. Daha sonra, [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) türü veya alt türü hakkında bilgi almak için _CrtReportBlockType'i kullanabilirsiniz.

 CRTDBG'de tanımlandığı `_CrtSetDumpClient` gibi, **işlevinizin işaretçisi** _CRT_DUMP_CLIENT türüne sahiptir. H:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kanca İşlevi Yazmada Hata Ayıklama](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 Örneği](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)