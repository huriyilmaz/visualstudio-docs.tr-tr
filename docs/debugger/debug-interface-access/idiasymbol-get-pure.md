---
description: İşlevin saf sanal olup olmadığını belirten bir bayrak verir.
title: IDiaSymbol::get_pure | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_pure method
ms.assetid: b61107e9-9144-4981-b7ef-58a339b80c58
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e72d37c25ce1df188978eeb8a755e8cdc83cad9a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635385"
---
# <a name="idiasymbolget_pure"></a>IDiaSymbol::get_pure
İşlevin saf sanal olup olmadığını belirten bir bayrak verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_pure ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] İşlev `TRUE` saf sanal ise döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
