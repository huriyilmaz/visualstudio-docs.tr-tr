---
description: Simgenin Microsoft ara dili (MSIL) koduna işaret edilip edilmeyeceğini belirten bir bayrak alır.
title: 'IDiaSymbol:: get_msil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_msil method
ms.assetid: 43a8e003-6856-4726-aa16-c0d4dae7299b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 322b01e97507da4940aea02fe461da0b19b7995c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155952"
---
# <a name="idiasymbolget_msil"></a>IDiaSymbol::get_msil
Simgenin Microsoft ara dili (MSIL) koduna işaret edilip edilmeyeceğini belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_msil ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` SIMGENIN MSIL kodunu ifade eder; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
