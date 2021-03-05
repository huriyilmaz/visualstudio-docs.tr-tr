---
description: Bir kare veri öğesini bir dizin aracılığıyla alır.
title: 'IDiaEnumFrameData:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c22983881c6f4e7d1bbb8e25ec6030d85411145c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149055"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Bir kare veri öğesini bir dizin aracılığıyla alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesinin dizini. Dizin, `count` `count` [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) yöntemi tarafından döndürülen 0 ile-1 aralığındadır.

 section

dışı İstenen çerçeve verisi öğesini temsil eden bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
