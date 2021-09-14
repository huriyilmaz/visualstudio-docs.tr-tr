---
description: Belirtilen yığın çerçevesinde belirtilen yığın adresinin üzerinde veya yakınında bir dönüş adresi arar.
title: IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f556ec473053e7a8ebba5c90760104d65fa76983
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626804"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Belirtilen yığın çerçevesinde belirtilen yığın adresinin üzerinde veya yakınında bir dönüş adresi arar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parametreler
 `frame`

[in] Geçerli yığın çerçevesini temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi.

 `startAddress`

[in] Aramaya başlamak için bir sanal bellek adresi.

 `ReturnAddress`

[out] en yakın işlev dönüş adresini adresine `startAddress` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
