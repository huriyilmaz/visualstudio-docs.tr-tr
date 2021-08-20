---
description: Görüntünün temel alınarak bellek konumunu alınır.
title: IDiaImageData::get_imageBase | Microsoft Docs
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129194"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Görüntünün temel alınarak bellek konumunu alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Önerilen görüntü temel değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntü tabanı çakışmaları nedeniyle, bir görüntü yüklendiğinde otomatik olarak kullanılmayan bir bellek konuma yeniden temel olabilir. Bu yöntem, derleme zamanında modülde depolanan temel ipucunu (önerilen bellek konumu) döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
