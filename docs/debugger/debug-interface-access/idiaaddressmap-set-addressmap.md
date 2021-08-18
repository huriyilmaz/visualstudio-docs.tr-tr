---
description: Görüntü düzeni çevirilerini desteklemek için bir adres haritası sağlar.
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dd73b8bad816556ac598bc4c2c115e29f660e0fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058930"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Görüntü düzeni çevirilerini desteklemek için bir adres haritası sağlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parametreler
 `cbData`

[in] Parametresinde öğelerin `data` sayısı.

 `data[]`

[in] Çeviri haritasını [tanımlayan DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) Yapısı yapıları dizisi.

 `imagetoSymbols`

[in] `TRUE` parametresi yeni görüntü düzeninden özgün düzene (hata ayıklama sembolleri tarafından `data` açıklandığı gibi) bir harita tanımlarsa. `FALSE` , `data` özgün düzenden alınan yeni görüntü düzenine bir eşledir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dia genellikle program veritabanı (.pdb) dosyasından adres çevirisi eşlemelerini alır. Bu değerler [eksikse, IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi iki kez çağrılır ve parametresi olarak ayarlanmış ve bir kez parametresi `imagetoSymbols` olarak `TRUE` `imagetoSymbols` `FALSE` ayarlanmıştır. Her iki çeviri eşlemesi de sağilmadıkça adres eşlemesi [çevirileri IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) yöntemi kullanılarak etkinleştirilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [DiaAddressMapEntry Yapısı](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
