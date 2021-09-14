---
description: Geçerli görüntü hizalamasını alın.
title: IDiaAddressMap::get_imageAlign | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f8afda829cadbaaea693ebd12b30d6dd3bb7c91c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630549"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Geçerli görüntü hizalamasını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Yürütülebilir dosyadan görüntü hizalama değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntüler, görüntünün yüklenme ve oluşturulma durumuna bağlı olarak belirli bellek sınırlarına hizalanır. Hizalama genellikle 1, 2, 4, 8, 16, 32 veya 64 byte sınırlarındadır. Görüntü hizalaması, [IDiaAddressMap::p ut_imageAlign yöntemine](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) yapılan bir çağrıyla ayarlanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
