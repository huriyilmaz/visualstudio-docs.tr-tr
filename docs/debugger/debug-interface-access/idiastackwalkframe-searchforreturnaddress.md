---
description: 'IDiaStackWalkFrame:: searchForReturnAddress, en yakın işlev dönüş adresi için belirtilen yığın çerçevesini arar.'
title: 'IDiaStackWalkFrame:: searchForReturnAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3fa964f5b91185b75d9d10f1be225084cb9253da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156869"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
En yakın işlev dönüş adresi için belirtilen yığın çerçevesini arar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT searchForReturnAddress ( 
   IDiaFrameData* frame,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Parametreler
 `frame`

'ndaki Geçerli yığın çerçevesini temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi.

 `returnAddress`

dışı En yakın işlev dönüş adresini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
