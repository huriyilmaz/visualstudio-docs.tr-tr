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
ms.openlocfilehash: 0fd938ff87b7060287e03a7facb6bf3582c20d9fb77ffad1a7a3606308e6f420
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380311"
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
