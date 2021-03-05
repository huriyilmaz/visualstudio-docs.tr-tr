---
description: Geçerli özellik kümesinden belirtilen özellikleri okur.
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: c7d0191d17074ec41b5fc73b3e33ba94b845a96e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148152"
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

'ndaki Dizide belirtilen özellik sayısı `rgpspec` . Sıfır ise, yöntem hiçbir özellik döndürmez, ancak `S_OK` başarı kodu olarak döner.

 `rgpspec`

'ndaki Okunacak özellikler dizisi. Özellikler, bir özellik KIMLIĞIYLE ya da isteğe bağlı bir dize adı ile belirtilebilir. Dizide belirli bir sırada özellikleri belirtmek gerekli değildir. Dizi yinelenen özellikler içerebilir ve basit özellikler için dönüşte yinelenen özellik değerlerine neden olur. Basit olmayan özellikler, bu dosyaları ikinci kez açma girişiminde erişim engellendi olarak döndürmelidir. Dizi, özellik kimliklerinin ve dize kimliklerinin bir karışımını içerebilir. Bu dizi en az `cpspec` sayıda özellik değerine sahip olmalıdır.

 `rgvar`

[in, out] `PROPVARIANT` Her bir özellik için değerlerle doldurulacak bir dizi yapı (Microsoft. VisualStudio. OLE. Interop ad alanında). Dizi en az `cpspec` öğe boyutunda olmalıdır. Çağıranın dizideki değerleri başlatması gerekmez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bir veya daha fazla özellik bulunmazsa döndürür. Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir özellik bulunmazsa dizideki karşılık gelen giriş `rgvar` `VARIANT` , türü ile bir içerir `VT_EMPTY` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
