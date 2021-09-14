---
description: İşlevin yığın çerçevesi çalışma zamanı hata denetimiyle derlenmiş olup olmadığını söyleyen bir değer alır. Bu , /RTC bayrağıdır.
title: IDiaSymbol::get_isRTCs | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 47f4ad2d6ac2265052d48af2c33471d9c03ae912
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725467"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol::get_isRTCs

İşlevin yığın çerçevesi çalışma zamanı hata denetimiyle derlenmiş olup olmadığını söyleyen bir değer döndürür. Bu , /RTC bayrağıdır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler

 `pRetVal`

[out] İşlevin yığın çerçevesi çalışma zamanı hata denetimiyle derlenmiş olup olmadığını belirten bir BOOL işaretçisi.

## <a name="return-value"></a>Dönüş Değeri

 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar

Bu yöntem, 2019 Visual Studio 16.10 Önizleme 2 sürümünden itibaren de destekleni.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
