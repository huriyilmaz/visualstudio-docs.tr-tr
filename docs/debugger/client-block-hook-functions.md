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
ms.openlocfilehash: 5b7b0ef177922f09239c8925ced1ca013e966c0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745714"
---
# <a name="client-block-hook-functions"></a>İstemci Blok Kanca İşlevleri
@No__t_0 blokları içinde depolanan verilerin içeriğini doğrulamak veya raporlamak istiyorsanız, bu amaçla özel olarak bir işlev yazabilirsiniz. Yazdığınız işlev, CRTDBG içinde tanımlandığı şekilde aşağıdakine benzer bir prototipi içermelidir. Olsun

```cpp
void YourClientDump(void *, size_t)
```

 Diğer bir deyişle, kanca işleviniz, ayırma bloğunun başlangıcına, ayırma boyutunu belirten bir **size_t** türü değeriyle birlikte **void** bir işaretçi kabul etmelidir ve `void` döndürür. Bunun dışında, içeriği size ait.

 [_Crtsetdumpclient](/cpp/c-runtime-library/reference/crtsetdumpclient)kullanarak kanca işlevinizi yükledikten sonra, `_CLIENT_BLOCK` bir blok her döküşinizde çağrılır. Daha sonra, döküklerden oluşan tür veya alt türü hakkında bilgi almak için [_Crtreportblocktype](/cpp/c-runtime-library/reference/crtreportblocktype) kullanabilirsiniz.

 @No__t_0 'e geçirdiğiniz işlevinizin işaretçisi, CRTDBG içinde tanımlanan **_CRT_DUMP_CLIENT**türüdür. Olsun

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 örneği](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)