---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0de3a87d62195ae28e83efefa641dde5667f0a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468331"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Bir kare veri öğesini bir dizin aracılığıyla alır.

## <a name="syntax"></a>Söz dizimi

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