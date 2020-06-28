---
title: 'IDiaSymbol:: get_stride | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3853c6883ed5feab420f0b689c0c614d57aecd7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461958"
---
# <a name="idiasymbolget_stride"></a>IDiaSymbol::get_stride
Matrisin ilerini alır veya bir dizi harcar.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_stride(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı İlerleme tutan bir işaretçisi `DWORD` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)