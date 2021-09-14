---
description: x86 platformları için yığın çerçevesi numaralayıcısını verir.
title: IDiaStackWalker::getEnumFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d85e52cea94045b7db84098dffa4e18b2a9d3da1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635409"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
x86 platformları için yığın çerçevesi numaralayıcısını verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametreler
 `pHelper`

[in] Yardımcı [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesi.

 `ppEnum`

[out] [IDiaStackFrame nesnelerinin listesini içeren bir IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) [nesnesi](../../debugger/debug-interface-access/idiastackframe.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Başka bir platformda yığın çerçevesi listesi almak için [IDiaStackWalker::getEnumFrames2 yöntemini](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
