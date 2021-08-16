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
ms.openlocfilehash: da6a492b30121a429b4c1ae5f5048b41cc9dcd8921e24a312dcc056371c8d211
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344927"
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

[in] Okunan bir özellik dizisi. Özellikler bir özellik kimliği veya isteğe bağlı bir dize adı ile belirtilebilir. Dizide belirli bir sırada özellikleri belirtmek gerekli değildir. dizisinde yinelenen özellikler olabilir ve bu da basit özellikler için dönüşte yinelenen özellik değerlerine neden olabilir. Basit olmayan özellikler, bunları ikinci kez açma girişiminde erişim reddedildi olarak geri dönmeli. dizisinde özellik kimlikleri ile dize kimliklerinin bir karışımı yer alır. Bu dizinin en az sayıda `cpspec` özellik değeri olması gerekir.

 `rgvar`

[in, out] Her özelliğin değerleriyle doldurulan bir yapı dizisi `PROPVARIANT` (Microsoft.VisualStudio.OLE.Interop ad alanında). Dizi en az `cpspec` boyuttaki öğelerden biri olmalı. Çağıranın dizide değerleri başlatması gerek değildir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Özelliklerden `S_FALSE` biri veya daha fazlası bulunamasa döndürür. Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir özellik bulunamasa, dizide karşılık gelen `rgvar` giriş `VARIANT` türüne sahip bir `VT_EMPTY` içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
