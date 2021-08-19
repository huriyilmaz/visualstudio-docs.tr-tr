---
description: Bu işaretçinin kısıtlanmış olarak işaretlenmiş olup olmadığını belirtir.
title: IDiaSymbol::get_restrictedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7070a619556871344558950cc48f43cb7b06c738
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147219"
---
# <a name="idiasymbolget_restrictedtype"></a>IDiaSymbol::get_restrictedType
İşaretçinin `this` kısıtlanmış olarak işaretlenmiş olup olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_restrictedType(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] İşaretçinin `BOOL` kısıtlanmış olarak `this` işaretlenmiş olup olmadığını belirten bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
