---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 257546e54cb04713f2f13892ec782aca1712cfba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466520"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.

## <a name="syntax"></a>Söz dizimi

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