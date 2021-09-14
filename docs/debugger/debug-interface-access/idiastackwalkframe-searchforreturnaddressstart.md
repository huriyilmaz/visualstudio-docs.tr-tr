---
description: Belirtilen yığın çerçevesinde belirtilen adreste veya yakınında bir dönüş adresi arar.
title: IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fd8070890752e08e265ee2f526964a871e848f76
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626853"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Belirtilen yığın çerçevesinde belirtilen adreste veya yakınında bir dönüş adresi arar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT searchForReturnAddressStart ( 
   IDiaFrameData* frame,
   ULONGLONG      startAddress,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Parametreler
 `frame`

[in] Geçerli yığın çerçevesini temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi.

 `startAddress`

[in] Aramaya başlamak için bir sanal bellek adresi.

 `returnAddress`

[out] en yakın işlev dönüş adresini adresine `startAddress` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
