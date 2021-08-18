---
description: Yöntemi için bu ayarlancı 'yi alır.
title: 'IDiaSymbol:: get_thisAdjust | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thisAdjust method
ms.assetid: 56b9a147-e8c0-4d4b-a42a-398214dd5f86
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7b4f166f936bef12c183eb7064d10f1c1d6217e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036066"
---
# <a name="idiasymbolget_thisadjust"></a>IDiaSymbol::get_thisAdjust
`this`Yöntemi için mantıksal ayarlanıcısı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_thisAdjust ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `this` Yöntemi için mantıksal ayarlanıcısı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bazı çoklu devralma durumlarında yöntemin kendisi `this` için bir konum ekleyerek doğru bir değeri hesaplaması gerekir `this` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
