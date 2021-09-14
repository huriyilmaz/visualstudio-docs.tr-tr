---
description: Sembol adreslerini çevirmek için adres eşlemesi kullanıp kullanılmay gerektiğini belirtir.
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f4c3a08361942df789c7e6bbd055464d69d056fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630542"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Sembol adreslerini çevirmek için adres eşlemesi kullanıp kullanılmay gerektiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

[in] Sembollerin `TRUE` çevirisini etkinleştirmek veya devre dışı bırakmak için `FALSE` olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yürütülebilir son işlemciler bazen yürütülebilir dosyayı güncelleştirebilir. DIA, sembollerin yeni düzene çevirisini destekleyen bir mekanizma içerir.

 Bir PDB dosyası yüklendiğinde, dosyada depolanan adres eşlemesi etkinleştirilir. Ancak bazen bir istemci uygulamanın [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemini çağırarak kendi adres haritasını temin set_addressMap olabilir. Yöntem başarılı olursa, istemci uygulamanın bu adres eşlemesi kullanımını etkinleştirmek için `set_addressMap` `put_addressMapEnabled` `NewVal` `TRUE` parametresiyle yöntemini çağırsı gerekir.

 Etkinleştirilen adres eşlemesi geçerli [durumu, IDiaAddressMap::get_addressMapEnabled yöntemi çağrısıyla](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) alınabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
