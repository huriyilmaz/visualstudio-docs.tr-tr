---
title: 'IDiaSymbol:: get_sizeInUdt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba2f0351997b5f6a2a96cb035871b116b9180786
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461986"
---
# <a name="idiasymbolget_sizeinudt"></a>IDiaSymbol::get_sizeInUdt
Kullanıcı tanımlı bir türün bir üyesinin boyutunu alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_sizeInUdt(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD`Üyenin boyutunu belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)