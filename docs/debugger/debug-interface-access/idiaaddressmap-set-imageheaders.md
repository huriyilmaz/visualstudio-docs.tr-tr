---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ded09d64a071c12e14de1597c21aad3872cacf4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468548"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Göreli sanal adres çevirisini etkinleştirmek için görüntü üst bilgilerini ayarlar.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parametreler
 cbData

'ndaki Üst bilgi verilerinin bayt sayısı. , `n*sizeof(IMAGE_SECTION_HEADER)` `n` Çalıştırılabilirteki bölüm üst bilgilerinin sayısıdır.

 veri []

'ndaki `IMAGE_SECTION_HEADER`Görüntü üst bilgileri olarak kullanılacak yapıların dizisi.

 originalHeaders

'ndaki `FALSE` `TRUE` Bir yükseltmeden önce orijinal görüntüyü yansıtalarsa, resim üstbilgileri yeni görüntüden ise olarak ayarlanır. Genellikle, bu, `TRUE` yalnızca [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metoduna yapılan çağrılarla birlikte ayarlanabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `IMAGE_SECTION_HEADER`Yapı, Winnt. h içinde bildirilmiştir ve yürütülebilir dosyanın görüntü bölümü üstbilgi biçimini temsil eder.

 Göreli sanal adres hesaplamaları `IMAGE_SECTION_HEADER` değerlere bağımlıdır. Genellikle, bu dosyaları program veritabanı (. pdb) dosyasından alır. Bu değerler eksikse, DIA göreli sanal adresleri ve [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemi döndürür `FALSE` . İstemci daha sonra, görüntünün kendisinden kayıp resim üstbilgilerini sağladıktan sonra göreli sanal adres hesaplamalarını etkinleştirmek için [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodunu çağırmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)