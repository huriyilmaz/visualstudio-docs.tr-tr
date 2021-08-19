---
description: Göreli sanal adres çevirisini etkinleştirmek için görüntü üst bilgilerini ayarlar.
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3acedb7cf87d9dac560f552a305fc736f7b570fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075040"
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
 Cbdata

[in] Üst bilgi verisi bayt sayısı. `n*sizeof(IMAGE_SECTION_HEADER)`Yürütülebilir `n` dosyada bölüm üst bilgisi sayısı burada olması gerekir.

 data[]

[in] Görüntü  `IMAGE_SECTION_HEADER` üst bilgileri olarak kullanılacak yapı dizisi.

 originalHeaders

[in] Yükseltmeden `FALSE` önce özgün görüntüyü yansıtıyorsa, görüntü üst bilgileri yeni görüntüdense olarak `TRUE` ayarlayın. Genellikle, bu yalnızca `TRUE` [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemine yapılan çağrılarla birlikte olarak ayarlanır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yapı `IMAGE_SECTION_HEADER` Winnt.h içinde bildirildi ve yürütülebilir dosyanın görüntü bölümü üst bilgi biçimini temsil eder.

 Göreli sanal adres hesaplamaları değerlere `IMAGE_SECTION_HEADER` bağlıdır. Dia genellikle bunları program veritabanı (.pdb) dosyasından alır. Bu değerler eksikse, DIA göreli sanal adresleri hesap yapamaz ve [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemi `FALSE` döndürür. İstemci daha sonra görüntünün kendisinde eksik görüntü üst bilgilerini verdikten sonra göreli sanal adres hesaplamalarını etkinleştirmek için [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) yöntemini çağırabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
