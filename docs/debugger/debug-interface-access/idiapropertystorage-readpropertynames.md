---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742865"
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

'ndaki @No__t_0 özellik kimliği sayısı.

 `rgpropid`

'ndaki Adların alınacağı özellik kimliklerinin dizisi (`PROPID` `ULONG` olarak WTypes. h içinde tanımlanmıştır).

 `rglpwstrName`

[in, out] Belirtilen özellik kimlikleri için özellik adları dizisi. Dizi, istenen özellik adı sayısını tutmak için önceden ayrılmış olmalıdır ve en az `cpropid``BSTR` dize tutabilecek olmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen özellik adları, artık gerekli olmadığında serbest bırakılmalıdır (`SysFreeString` işlevi çağırarak).

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)