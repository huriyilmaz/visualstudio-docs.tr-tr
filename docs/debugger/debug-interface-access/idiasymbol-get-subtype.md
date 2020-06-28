---
title: 'IDiaSymbol:: get_subType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0b3cbf77-8f11-434a-ad60-ea9829fec6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57a7756d7764cbd4799bfe49eec7f06732bd0bee
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461951"
---
# <a name="idiasymbolget_subtype"></a>IDiaSymbol::get_subType
Alt türü alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_subType(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Alt türe yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)