---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745008"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Göreli sanal adres çevirisini etkinleştirmek için görüntü üst bilgilerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parametreler
 cbData

'ndaki Üst bilgi verilerinin bayt sayısı. @No__t_0, çalıştırılabilir dosya `n` bölüm üst bilgilerinin sayısıdır.

 veri []

'ndaki Görüntü üst bilgileri olarak kullanılacak `IMAGE_SECTION_HEADER` yapılarından oluşan bir dizi.

 originalHeaders

'ndaki Görüntünün üst bilgileri yeni görüntüden ise, bir yükseltmeden önce orijinal görüntüyü yansıtdıklarında, `TRUE` `FALSE` olarak ayarlayın. Genellikle, bu, yalnızca [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metoduna yapılan çağrılarla birlikte `TRUE` olarak ayarlanır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 yapısı, Winnt. h içinde bildirilmiştir ve yürütülebilir dosyanın görüntü bölümü üstbilgi biçimini temsil eder.

 Göreli sanal adres hesaplamaları `IMAGE_SECTION_HEADER` değerlere bağımlıdır. Genellikle, bu dosyaları program veritabanı (. pdb) dosyasından alır. Bu değerler eksikse, DIA göreli sanal adresleri hesaplayamaz ve [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemi `FALSE` döndürür. Daha sonra istemci, görüntünün kendisinden kayıp resim üstbilgilerini sağladıktan sonra göreli sanal adres hesaplamalarını etkinleştirmek için [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodunu çağırmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)