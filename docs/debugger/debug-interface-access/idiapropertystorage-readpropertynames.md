---
description: Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbb6d511a6be9ed408b076162a3d00d22705075a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148145"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parametreler
 `cpropid`

'ndaki İçindeki özellik kimliği sayısı `rgpropid` .

 `rgpropid`

'ndaki Adların alınacağı özellik kimliklerinin dizisi ( `PROPID` WTypes. h olarak bir olarak tanımlanır `ULONG` ).

 `rglpwstrName`

[in, out] Belirtilen özellik kimlikleri için özellik adları dizisi. Dizi, istenen özellik adı sayısını tutmak için önceden ayrılmış olmalıdır ve en az dizeleri tutabilecek olmalıdır `cpropid``BSTR` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen özellik adları artık gerekli olmadığında serbest bırakılmalıdır (işlevi çağırarak `SysFreeString` ).

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
