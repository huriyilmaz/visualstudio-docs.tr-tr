---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745022"
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

'ndaki `data` parametresindeki öğelerin sayısı.

 `data[]`

'ndaki Çeviri eşlemesini tanımlayan [DiaAddressMapEntry yapı](../../debugger/debug-interface-access/diaaddressmapentry.md) yapılarının dizisi.

 `imagetoSymbols`

[in] `data` parametresi yeni görüntü düzeninden özgün düzene (hata ayıklama sembolleri tarafından açıklandığı gibi) bir harita tanımlıyorsa `TRUE`. `data` özgün düzenden alınan yeni görüntü düzenine bir eşleme ise `FALSE`.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, genellikle, program veritabanı (. pdb) dosyasındaki adres çevirisi haritalarını alır. Bu değerler eksikse, [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi iki kez çağrılır, `imagetoSymbols` parametresi `TRUE` ve bir kez `imagetoSymbols` parametresi `FALSE`olarak ayarlanır. Her iki çeviri eşlemesi sağlanmamışsa, [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) yöntemi kullanılarak adres Haritası çevirileri etkinleştirilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [DiaAddressMapEntry Yapısı](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)