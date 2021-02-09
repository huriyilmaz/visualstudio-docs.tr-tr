---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 4c4a450522ea97ee5b0b11993e8e4b6474de4a9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857176"
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

'ndaki Parametresindeki öğelerin sayısı `data` .

 `data[]`

'ndaki Çeviri eşlemesini tanımlayan [DiaAddressMapEntry yapı](../../debugger/debug-interface-access/diaaddressmapentry.md) yapılarının dizisi.

 `imagetoSymbols`

[in] `TRUE` `data` parametresi yeni görüntü düzeninden özgün düzene (hata ayıklama sembolleri tarafından açıklandığı gibi) bir harita tanımlıyorsa. `FALSE` , `data` özgün düzenden alınan yeni görüntü düzenine bir haritadır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, genellikle, program veritabanı (. pdb) dosyasındaki adres çevirisi haritalarını alır. Bu değerler eksikse, [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi iki kez çağrılır; parametresi olarak ayarlanmış `imagetoSymbols` `TRUE` parametresi ile bir kez olarak ayarlanır `imagetoSymbols` `FALSE` . Her iki çeviri eşlemesi sağlanmamışsa, [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) yöntemi kullanılarak adres Haritası çevirileri etkinleştirilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [DiaAddressMapEntry Yapısı](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)