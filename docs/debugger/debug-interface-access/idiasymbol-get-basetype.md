---
title: IDiaSymbol::get_baseType
description: Bu simge için temel türü alma
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f3fe85f37d75db8a86f544908e23a0a229992e89
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980488"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
Bu simge için temel türü alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
`pRetVal`

[out] Sembolün temel türünü [belirten BasicType Enumeration](../../debugger/debug-interface-access/basictype.md) numaralarından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
Bir simgenin temel türü, önce sembolün türünü alma ve ardından temel tür için döndürülen türü sorgulama ile belirlenecektir. Bazı sembollerin bir temel türü (yapı adı gibi) olmadığını unutmayın.

## <a name="example"></a>Örnek

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType Numaralandırması](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
