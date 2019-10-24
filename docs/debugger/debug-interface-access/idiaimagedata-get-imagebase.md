---
title: 'IDiaImageData:: get_imageBase | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743445"
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
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntü tabanı çakışmaları nedeniyle, bir görüntü yüklendiğinde kullanılmayan bellek konumuna otomatik olarak yeniden dayalı olabilir. Bu yöntem, derleme zamanında modülünde depolanan temel ipucunu (önerilen bellek konumu) döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)