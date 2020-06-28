---
title: 'IDiaSymbol:: get_symIndexId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symIndexId method
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe5c412e815b5cda02959f792197954cb1f92540
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461923"
---
# <a name="idiasymbolget_symindexid"></a>IDiaSymbol::get_symIndexId
Benzersiz sembol tanımlayıcısını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_symIndexId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Simgenin sembol KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek için DIA SDK tarafından oluşturulan benzersiz bir değerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)