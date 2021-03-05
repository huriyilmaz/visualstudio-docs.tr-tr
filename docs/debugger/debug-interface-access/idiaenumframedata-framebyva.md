---
description: Sanal adrese (VA) göre bir çerçeve döndürür.
title: 'IDiaEnumFrameData:: frameByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2fa167749574165df2a7acffdc232e3fd4c66e4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158080"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Sanal adrese (VA) göre bir çerçeve döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametreler
 virtualAddress

'ndaki İlgilendiğiniz çerçevenin VA.

 çerçeve

dışı Belirtilen adresi içeren çerçeveyi temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Belirtilen adresle eşleşen hiçbir çerçeve verisi yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
