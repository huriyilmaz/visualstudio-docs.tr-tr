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
ms.openlocfilehash: bacfab75a01ae0923c4fce7c696eabdfbfd572622678d3436baf41cfd0974e71
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345359"
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
 Görüntüler, görüntünün yüklenme ve oluşturulma durumuna bağlı olarak belirli bellek sınırlarına hizalanır. Hizalama genellikle 1, 2, 4, 8, 16, 32 veya 64 byte sınırları üzerindedir. Görüntü hizalaması, [IDiaAddressMap::p ut_imageAlign yöntemine](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) yapılan bir çağrıyla ayarlanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
