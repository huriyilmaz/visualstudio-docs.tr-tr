---
description: Alt tür KIMLIĞINI alır.
title: 'IDiaSymbol:: get_subTypeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0f899920-4fc5-4de8-84a3-cd98c57bf124
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d12c5308513f015b7fcc99b8073e138092d43ffc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081112"
---
# <a name="idiasymbolget_subtypeid"></a>IDiaSymbol::get_subTypeId
Alt tür KIMLIĞINI alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_subTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD` Alt tür kimliğini tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
