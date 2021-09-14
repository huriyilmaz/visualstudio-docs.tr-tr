---
description: Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c49a688fe1ecf9892ec5943934749694e8a839b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629523"
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

[in] içinde özellik kimliklerinin `rgpropid` sayısı.

 `rgpropid`

[in] Adların ( WTypes.h içinde bir olarak tanımlanır) almak için `PROPID` özellik kimlikleri `ULONG` dizisi.

 `rglpwstrName`

[in, out] Belirtilen özellik kimlikleri için özellik adları dizisi. Dizi, istenen özellik adlarını tutmak için önceden ayrılmış olmalı ve en azından dizeleri `cpropid``BSTR` tutabilecektir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen özellik adları artık gerekli olmadığı zaman serbest bırak (işlevi `SysFreeString` çağırarak) gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
