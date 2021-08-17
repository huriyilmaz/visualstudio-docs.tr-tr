---
description: Bu işaretçinin birden çok devralmaya sahip bir veri üyesine işaret edip ede olmadığını belirtir.
title: IDiaSymbol::get_isMultipleInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b64d22dea62ceaf20162c3e4734bc057b54213d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044137"
---
# <a name="idiasymbolget_ismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
İşaretçinin birden `this` çok devralmaya sahip bir veri üyesine işaret edip ede olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] İşaretçinin `BOOL` birden çok devralmaya sahip bir `this` veri üyesine işaret edip olmadığını belirten bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
