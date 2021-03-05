---
description: Bir sanal temel tablo işaretçisinin türünü alır.
title: 'IDiaSymbol:: get_virtualBaseTableType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67affafd1984f811432a0b69fdcdfec0521e377
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155518"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Bir sanal temel tablo işaretçisinin türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|`pRetVal`|dışı Temel tablo türünü belirten bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.|

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sanal temel tablo işaretçisi ( `vbtptr` ), [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] sanal temel sınıflardan devralmayı işleyen bir vtable 'da gizli bir işaretçidir. , `vbtptr` Devralınan sınıflara bağlı olarak farklı boyutlarda olabilir.

 Bu yöntem, vbtptr boyutunu belirlemekte kullanılabilecek bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
