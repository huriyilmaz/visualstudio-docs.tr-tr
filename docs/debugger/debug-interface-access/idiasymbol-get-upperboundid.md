---
description: Bir FORTRAN dizi boyutunun üst sınırının sembol tanımlayıcısını alır.
title: 'IDiaSymbol:: get_upperBoundId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c0d5bb2206293a560adb049afff5430a083c9ab2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081072"
---
# <a name="idiasymbolget_upperboundid"></a>IDiaSymbol::get_upperBoundId
Bir FORTRAN dizi boyutunun üst sınırının sembol tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`
- [Out,] Bir FORTRAN dizi boyutunun üst sınırını temsil eden simgenin KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek için DIA SDK tarafından oluşturulan benzersiz bir değerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
