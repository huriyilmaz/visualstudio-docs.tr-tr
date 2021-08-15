---
description: Görüntü hizalamasını ayarlar.
title: IDiaAddressMap::p ut_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7802d2dd19b5dfe8e4aed9acb56ef6bc7a3198d946d950ee99d8e6ba69e975a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326372"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Görüntü hizalamasını ayarlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

[in] Yürütülebilir dosya için yeni görüntü hizalama değeri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntüler (yüklenen yürütülebilir dosyalar) belirtilen bellek sınırlarına hizalanır. Bu hizalama geçerli sistem mimarisi ve derleme ve bağlantı zamanı seçenekleri tarafından etkilenebilir. Görüntü hizalama her zaman byte sınırlardadır. Aşağıdaki görüntü hizalama değerleri geçerlidir: 1, 2, 4, 8, 16, 32 ve 64 byte sınırları.

 Geçerli görüntü hizalaması, [IDiaAddressMap::get_imageAlign yöntemi çağrısıyla](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) alınabilirsiniz.

> [!NOTE]
> Bu yöntem çağrılana kadar görüntü zaten yüklenmiştir. yöntemi `put_imageAlign` genellikle görüntü taşındığında veya değiştiriken ve yeni bir hizalama gerektiğinde kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
