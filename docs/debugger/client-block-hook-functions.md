---
title: İstemci blok kanca Işlevleri | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881809dda7e8254f9d337b68f0c317eccfd9093d
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600203"
---
# <a name="client-block-hook-functions"></a>İstemci Blok Kanca İşlevleri
Bloklar halinde depolanan verilerin içeriğini doğrulamak veya raporlamak isterseniz `_CLIENT_BLOCK` , bu amaçla özel olarak bir işlev yazabilirsiniz. Yazdığınız işlev, CRTDBG içinde tanımlandığı şekilde aşağıdakine benzer bir prototipi içermelidir. Olsun

```cpp
void YourClientDump(void *, size_t)
```

 Diğer bir deyişle, kanca işleviniz, ayırma bloğunun başlangıcına, ayırma boyutunu belirten bir **size_t** tür değeriyle birlikte bir **void** işaretçisi kabul etmelidir ve döndürülür `void` . Bunun dışında, içeriği size ait.

 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanarak kanca işlevinizi yükledikten sonra, bir `_CLIENT_BLOCK` blok her döküşinizde çağrılacaktır. Daha sonra, dökübir blok türü veya alt türü hakkında bilgi almak için [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) kullanabilirsiniz.

 İşlevinizin geçirdiğiniz işaretçi, `_CrtSetDumpClient` CRTDBG içinde tanımlandığı gibi **_CRT_DUMP_CLIENT**türündedir. Olsun

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 örneği](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)