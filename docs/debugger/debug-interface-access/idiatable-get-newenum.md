---
description: Tablo numaralayıcının System.Runtime.InteropServices.ComTypes.IEnumVARIANT sürümünü alır.
title: IDiaTable::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f64cc5b239c571cb08cf7ce6fef451ed2935f2d773e54a9dff1ac9f625b1348c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420407"
---
# <a name="idiatableget__newenum"></a>IDiaTable::get__NewEnum
Bu <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> numaralayıcının sürümünü alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bu `IUnknown` numaralayıcının <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> sürümünü temsil eden arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
