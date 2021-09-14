---
description: Görüntünün dayanmanız gereken bellek konumunu alır.
title: 'IDiaImageData:: get_imageBase | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 699ad3a289ff790c414a4c3e8a552436a22ab633
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629786"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Görüntünün dayanmanız gereken bellek konumunu alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Önerilen görüntü taban değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntü tabanı çakışmaları nedeniyle, bir görüntü yüklendiğinde kullanılmayan bellek konumuna otomatik olarak yeniden dayalı olabilir. Bu yöntem, derleme zamanında modülünde depolanan temel ipucunu (önerilen bellek konumu) döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
