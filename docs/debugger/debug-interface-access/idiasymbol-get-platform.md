---
description: Derlemenin derlenmiş olduğu platform türünü alın.
title: IDiaSymbol::get_platform | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c05237056b826ec47978f01e5f2258ae19b157b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635390"
---
# <a name="idiasymbolget_platform"></a>IDiaSymbol::get_platform
Derlemenin derlenmiş olduğu platform türünü alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_platform ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Derlemenin [derlenmiş olduğu](../../debugger/debug-interface-access/cv-cpu-type-e.md) platform türünü belirten CV_CPU_TYPE_e enumeration enumeration değerinden bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_CPU_TYPE_e Numaralandırması](../../debugger/debug-interface-access/cv-cpu-type-e.md)
