---
title: 'Idiastackdenetçisi:: getEnumFrames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd6f5219edf9426067a4431936caa2186604e1cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741546"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
X86 platformları için bir yığın çerçeve numaralandırıcısı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametreler
 `pHelper`

'ndaki Yardımcı [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesi.

 `ppEnum`

dışı [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) nesnelerinin bir listesini Içeren bir [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Başka herhangi bir platformda yığın çerçeve listesi almak için, [ıdiastackdenetçisi:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)