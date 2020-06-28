---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad9a97dd2e50b5bc131975321306bf8d9d52501e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468569"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Resim hizalamasını ayarlar.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

'ndaki Yürütülebilir dosya için yeni resim hizalama değeri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntüler (yüklenen yürütülebilir dosyalar) belirtilen bellek sınırlarına hizalanır. Bu hizalama, geçerli sistem mimarisinden ve derleme ve bağlama zaman seçenekleriyle etkilenebilir. Görüntü hizalaması her zaman bayt sınırlarında. Şu resim hizalama değerleri geçerli: 1, 2, 4, 8, 16, 32 ve 64 bayt sınırları.

 Geçerli görüntü hizalaması [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) yöntemi çağrısıyla alınabilir.

> [!NOTE]
> Görüntü, bu yöntemin çağrılabilecek zaman tarafından zaten yüklenmiş. `put_imageAlign`Yöntemi genellikle görüntü taşındığında veya değiştirildiğinde ve yeni bir hizalama gerektiğinde kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)