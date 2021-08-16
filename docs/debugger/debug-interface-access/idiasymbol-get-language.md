---
description: Kaynağın dilini alan.
title: IDiaSymbol::get_language | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06bdf7fdbda25d383084a0c53b224ccb5b8c64d12af79096e6edcf7fbb68e40e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379841"
---
# <a name="idiasymbolget_language"></a>IDiaSymbol::get_language
Kaynağın dilini alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_language ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Kaynak dilini [CV_CFL_LANG enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md) enumeration'dan bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_CFL_LANG Numaralandırması](../../debugger/debug-interface-access/cv-cfl-lang.md)
