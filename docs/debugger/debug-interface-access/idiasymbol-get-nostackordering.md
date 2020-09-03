---
title: 'IDiaSymbol:: get_noStackOrdering | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c82b8c4836d97f02fa84aec500d961911f993df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462793"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
Bu işlev, yığın arabelleği denetiminin ([/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) derleyici seçeneği) bir parçası olarak yığın sıralaması yapılıp yapılmayacağını belirten bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Yığın `TRUE` arabelleği denetiminin bir parçası olarak yığın sıralaması yapılamadığını, aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Description|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check)