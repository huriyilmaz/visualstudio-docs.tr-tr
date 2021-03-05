---
description: Bu işaretçinin birden çok devralmayla bir veri üyesine işaret ettiğini belirtir.
title: 'IDiaSymbol:: get_isMultipleInheritance | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d197810c61ca50a98cc47c5c3e2ecaca5be548d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156176"
---
# <a name="idiasymbolget_ismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
`this`İşaretçinin birden çok devralmayla bir veri üyesine işaret ettiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` `this` İşaretçinin birden çok Devralmada bir veri üyesine işaret ettiğini belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
