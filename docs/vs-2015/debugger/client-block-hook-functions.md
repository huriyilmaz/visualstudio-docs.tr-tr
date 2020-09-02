---
title: İstemci blok kanca Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702333"
---
# <a name="client-block-hook-functions"></a>İstemci Blok Kanca İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bloklar halinde depolanan verilerin içeriğini doğrulamak veya raporlamak isterseniz `_CLIENT_BLOCK` , bu amaçla özel olarak bir işlev yazabilirsiniz. Yazdığınız işlev, CRTDBG içinde tanımlandığı şekilde aşağıdakine benzer bir prototipi içermelidir. Olsun  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Diğer bir deyişle, kanca işleviniz, ayırma bloğunun başlangıcına, ayırma boyutunu belirten bir **size_t** tür değeriyle birlikte bir **void** işaretçisi kabul etmelidir ve döndürülür `void` . Bunun dışında, içeriği size ait.  
  
 [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)kullanarak kanca işlevinizi yükledikten sonra, bir `_CLIENT_BLOCK` blok her döküşinizde çağrılacaktır. Daha sonra, dökübir blok türü veya alt türü hakkında bilgi almak için [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) kullanabilirsiniz.  
  
 İşlevinizin geçirdiğiniz işaretçi, `_CrtSetDumpClient` CRTDBG içinde tanımlandığı gibi **_CRT_DUMP_CLIENT**türündedir. Olsun  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 örneği](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
