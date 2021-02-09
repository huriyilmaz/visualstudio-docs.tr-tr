---
title: 'IDiaStackWalkFrame:: searchForReturnAddressStart | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 7df2a6bf560c8b0916357c063dff01f1d8f5ac9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854775"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Belirtilen adreste veya yakınında bir dönüş adresi için belirtilen yığın çerçevesini arar.

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

'ndaki Geçerli yığın çerçevesini temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi.

 `startAddress`

'ndaki Aramanın başlatılacağı bir sanal bellek adresi.

 `returnAddress`

dışı En yakın işlev dönüş adresini döndürür `startAddress` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)