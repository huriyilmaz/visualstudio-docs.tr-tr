---
title: 'IDiaSymbol:: get_callingConvention | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1b0581e7a49ac8c8681077a7f40133498a48789
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740885"
---
# <a name="idiasymbolget_callingconvention"></a>IDiaSymbol::get_callingConvention
Yöntem çağırma yöntemi göstergesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_callingConvention ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Yöntemin çağırma kuralını belirten [CV_call_e sabit](../../debugger/debug-interface-access/cv-call-e.md) listesi numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_call_e Numaralandırması](../../debugger/debug-interface-access/cv-call-e.md)