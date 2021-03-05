---
description: Geçerli resim hizalamasını alır.
title: 'IDiaAddressMap:: get_imageAlign | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: daf52fa451c690445778258400f68ad95cc91f3c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151157"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Geçerli resim hizalamasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Yürütülebilir dosyadan resim hizalama değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntüler, görüntünün yüklenme ve oluşturulma şekline bağlı olarak belirli bellek sınırlarına hizalanır. Hizalama genellikle 1, 2, 4, 8, 16, 32 veya 64 baytlık sınırlardır. Görüntü hizalaması [IDiaAddressMap::p ut_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) yöntemi çağrısıyla ayarlanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
