---
title: 'IDiaSymbol:: get_targetOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetOffset method
ms.assetid: 7d141223-132a-409c-a5a4-94f97340313c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 104bc82785e297d397d4aadf44a64dbe4f2e12df
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461860"
---
# <a name="idiasymbolget_targetoffset"></a>IDiaSymbol::get_targetOffset
Bir dönüştürücü hedefinin konum bölümünü alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_targetOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir dönüştürücü hedef adresinin konum kısmını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)