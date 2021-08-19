---
description: Bir veri sembolünün konum türünü alır.
title: 'IDiaSymbol:: get_locationType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_locationType method
ms.assetid: fbb09c43-ebb7-4b4f-be53-ccff86eb183a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fec2412b7b8801f1197bc53963b5166cb2cc950f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147282"
---
# <a name="idiasymbolget_locationtype"></a>IDiaSymbol::get_locationType
Bir veri sembolünün konum türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_locationType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı , Veya gibi bir veri sembolünün konum türünü belirten [LocationType sabit](../../debugger/debug-interface-access/locationtype.md) listesi numaralandırmasından bir değer döndürür `static` `local` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
