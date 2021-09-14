---
description: Belirtilen özellikleri geçerli özellik kümesinden okur.
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1594d7137ec6c34c794f588f7a126bdb1392462b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629546"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Belirtilen özellikleri geçerli özellik kümesinden okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parametreler
 `cpspec`

[in] Dizide belirtilen özelliklerin `rgpspec` sayısı. Sıfır ise, yöntemi özellik döndüren değil bir başarı `S_OK` kodu olarak döndürür.

 `rgpspec`

[in] Okunan özellikler dizisi. Özellikler bir özellik kimliği veya isteğe bağlı bir dize adı ile belirtilebilir. Dizide belirli bir sırada özellikleri belirtmek gerekli değildir. dizisinde yinelenen özellikler olabilir ve bu da basit özellikler için dönüşte yinelenen özellik değerlerine neden olabilir. Basit olmayan özellikler, bunları ikinci kez açma girişiminde erişim reddedildi olarak iade etmek zorunda. dizisinde özellik kimlikleri ile dize kimliklerinin bir karışımı yer alır. Bu dizinin en az sayıda `cpspec` özellik değeri olması gerekir.

 `rgvar`

[in, out] Her özelliğin değerleriyle doldurulan bir yapı dizisi `PROPVARIANT` (Microsoft.VisualStudio.OLE.Interop ad alanında). Dizi en az `cpspec` boyuttaki öğelerden biri olmalı. Çağıranın dizide değerleri başlatması gerek değildir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Özelliklerden `S_FALSE` biri veya daha fazlası bulunamasa döndürür. Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir özellik bulunamasa, dizide karşılık gelen `rgvar` girdi `VARIANT` türüne sahip bir `VT_EMPTY` içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
