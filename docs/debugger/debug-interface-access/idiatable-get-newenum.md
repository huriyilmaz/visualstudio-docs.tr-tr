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
ms.openlocfilehash: 6b2100424fc131502b58a7f4c73ab63fc6a8ac19
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121220"
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
