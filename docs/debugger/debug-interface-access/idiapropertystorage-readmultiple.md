---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742879"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Geçerli özellik kümesinden belirtilen özellikleri okur.

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

'ndaki `rgpspec` dizisinde belirtilen özellik sayısı. Sıfır ise, yöntem hiçbir özellik döndürmez, ancak `S_OK` başarı kodu olarak döndürür.

 `rgpspec`

'ndaki Okunacak özellikler dizisi. Özellikler, bir özellik KIMLIĞIYLE ya da isteğe bağlı bir dize adı ile belirtilebilir. Dizide belirli bir sırada özellikleri belirtmek gerekli değildir. Dizi yinelenen özellikler içerebilir ve basit özellikler için dönüşte yinelenen özellik değerlerine neden olur. Basit olmayan özellikler, bu dosyaları ikinci kez açma girişiminde erişim engellendi olarak döndürmelidir. Dizi, özellik kimliklerinin ve dize kimliklerinin bir karışımını içerebilir. Bu dizide en az sayıda özellik değeri olmalıdır `cpspec`.

 `rgvar`

[in, out] Her bir özellik için değerlerle doldurulacak `PROPVARIANT` yapıları dizisi (Microsoft. VisualStudio. OLE. Interop ad alanında). Dizi en az `cpspec` öğe boyutunda olmalıdır. Çağıranın dizideki değerleri başlatması gerekmez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür. Bir veya daha fazla özellik bulunmazsa `S_FALSE` döndürür. Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir özellik bulunmazsa, `rgvar` dizisindeki karşılık gelen giriş `VT_EMPTY`türünde bir `VARIANT` içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)