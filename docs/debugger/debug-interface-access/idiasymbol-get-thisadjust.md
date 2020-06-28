---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2475ccf14d892a7f7d1b130c63dbea458038dd41
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461804"
---
# <a name="idiasymbolget_thisadjust"></a>IDiaSymbol::get_thisAdjust
`this`Yöntemi için mantıksal ayarlanıcısı alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_thisAdjust ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `this`Yöntemi için mantıksal ayarlanıcısı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bazı çoklu devralma durumlarında yöntemin kendisi `this` için bir konum ekleyerek doğru bir değeri hesaplaması gerekir `this` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)