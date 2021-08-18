---
description: Sembol dosyasının C türleri içerdiğini belirten bir bayrak alınır.
title: IDiaSymbol::get_isCTypes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 85a75e87b759a84c70f8d4f92d455a6d9a4e8cc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044145"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
Sembol dosyasının C türleri içerdiğini belirten bir bayrak alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isCTypes(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] Sembol `TRUE` dosyası C türleri içeriyorsa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik sembol türünden `SymTagExe` kullanılabilir (bkz. [Exe).](../../debugger/debug-interface-access/exe.md)

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
