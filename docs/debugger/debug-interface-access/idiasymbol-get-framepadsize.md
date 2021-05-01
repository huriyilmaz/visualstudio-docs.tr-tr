---
description: Her işleve eklenen ek Pad boyutunu alır.
title: 'IDiaSymbol:: get_framePadSize | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217248"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol:: get_framePadSize

Her işleve eklenen ek Pad boyutunu alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametreler

 `pPadSize`

dışı Her işleve eklenen ek Pad boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri

 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

Ek Panel boyutu genellikle Düzenle ve devam et tarafından kullanılır.

Bu yöntem, Visual Studio 2019 sürüm 16,10 Preview 2 ' den itibaren desteklenir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
