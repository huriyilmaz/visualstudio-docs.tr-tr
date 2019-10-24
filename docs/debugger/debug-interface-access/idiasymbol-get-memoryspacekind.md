---
title: 'IDiaSymbol:: get_memorySpaceKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d146df46defd0b0d052e0d65d5c40ae58a404d6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739796"
---
# <a name="idiasymbolget_memoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
Bellek alanı türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_memorySpaceKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bellek alanı türünü tutan `DWORD` için bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)