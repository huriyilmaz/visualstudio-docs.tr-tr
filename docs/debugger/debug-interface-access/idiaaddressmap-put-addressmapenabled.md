---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745059"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Adres eşlemesinin sembol adreslerini çevirmek için kullanılıp kullanılmayacağını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

'ndaki Simgelerin çevirisini etkinleştirmek için `TRUE` olarak ayarlayın veya devre dışı bırakmak için `FALSE`.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yürütülebilir son işlemciler bazen yürütülebilir dosyayı güncelleştirebilir. DIA, sembollerin yeni düzene çevirisini desteklemek için bir mekanizma içerir.

 Bir PDB dosyası yüklendiğinde, dosyada depolanan adres eşlemesi etkinleştirilir. Ancak, bir istemci uygulamanın [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemini çağırarak kendi adres haritasını sağlaması gerekebilecek durumlar vardır. `set_addressMap` yöntemi başarılı olursa, istemci uygulamanın bu adres eşlemesinin kullanımını etkinleştirmek için bir `NewVal` `TRUE` parametresiyle `put_addressMapEnabled` yöntemini çağırması gerekir.

 Etkin olan adres eşlemesinin geçerli durumu [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) yöntemi çağrısıyla alınabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)