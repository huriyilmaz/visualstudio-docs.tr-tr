---
description: Örnekleyici yuvasını alır.
title: 'IDiaSymbol:: get_samplerSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ae3ebd4944c71a72ad5d79ae26f86b9ea9978f13
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147161"
---
# <a name="idiasymbolget_samplerslot"></a>IDiaSymbol::get_samplerSlot
Örnekleyici yuvasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_samplerSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD` Örnekleyici yuvasını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
