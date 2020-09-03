---
title: 'IDiaInjectedSource:: get_crc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b67072fe2928556d355aac2e65cf5d011873edd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467129"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
Kaynak kodun baytlarından hesaplanan Döngüsel artıklık denetimi (CRC) alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kaynak kodun baytlarından hesaplanan CRC 'yi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)