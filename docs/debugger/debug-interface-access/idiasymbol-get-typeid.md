---
title: 'IDiaSymbol:: get_typeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeId method
ms.assetid: b40be36e-10e1-463c-9c6d-21862679d29f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d9c8f559e86e0acfb4137df61b82e28d21d3dfc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461714"
---
# <a name="idiasymbolget_typeid"></a>IDiaSymbol::get_typeId
Simgenin tür tanımlayıcısını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_typeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Simgenin tür KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek için DIA SDK tarafından oluşturulan benzersiz bir değerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)