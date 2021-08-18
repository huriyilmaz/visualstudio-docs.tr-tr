---
description: Kayıt dizinlerinin sayısını alır.
title: 'IDiaSymbol:: get_numberOfRegisterIndices | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3273237604b6a352eb5469fce123d0211590a909
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121364"
---
# <a name="idiasymbolget_numberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
Kayıt dizinlerinin sayısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_numberOfRegisterIndices(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD` Kayıt dizinlerinin sayısını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
