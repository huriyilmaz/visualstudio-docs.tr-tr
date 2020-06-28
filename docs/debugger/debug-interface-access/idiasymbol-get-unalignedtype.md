---
title: 'IDiaSymbol:: get_unalignedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unalignedType method
ms.assetid: fdcb38fb-490e-4d15-b4e5-3770043a366c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b42ec7b0026c19ab9ef9545a821179273bbb72c5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461618"
---
# <a name="idiasymbolget_unalignedtype"></a>IDiaSymbol::get_unalignedType
Kullanıcı tanımlı veri türünün hizalanmamış olup olmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_unalignedType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE`Kullanıcı tanımlı veri türü hizalanmamış ise döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)