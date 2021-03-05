---
description: Kullanıcı tanımlı bir tür için sanal tablo türünün sembol arabirimini alır.
title: 'IDiaSymbol:: get_virtualTableShape | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShape method
ms.assetid: 92360cbd-0761-446e-93f9-04dc8f4b66c6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f9d91e993a85f97acd23d396f40e4b1b82c9434
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155497"
---
# <a name="idiasymbolget_virtualtableshape"></a>IDiaSymbol::get_virtualTableShape
Kullanıcı tanımlı bir tür için sanal tablo türünün sembol arabirimini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_virtualTableShape ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kullanıcı tanımlı bir tür için sanal tabloyu temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
