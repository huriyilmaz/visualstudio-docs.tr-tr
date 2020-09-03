---
title: 'IDiaSymbol:: get_packed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73694e46f66014c251dbe3760dfade7baea566da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462590"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
Kullanıcı tanımlı veri türünün (UDT) paketlenemeyeceğini belirten bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Udt paketlense döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Paketlenmiş tüm UDT üyeleri, bellek sınırlarına hizalamak için araya giren bir doldurma olmadan mümkün olduğunca yakın şekilde konumlandırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)