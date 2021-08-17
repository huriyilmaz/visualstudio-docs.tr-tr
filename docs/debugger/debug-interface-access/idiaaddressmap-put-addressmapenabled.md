---
description: Adres eşlemesinin sembol adreslerini çevirmek için kullanılıp kullanılmayacağını belirtir.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105580"
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

'ndaki `TRUE` Simgelerin çevirisini etkinleştirmek veya devre dışı bırakmak için olarak ayarlayın `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yürütülebilir son işlemciler bazen yürütülebilir dosyayı güncelleştirebilir. DIA, sembollerin yeni düzene çevirisini desteklemek için bir mekanizma içerir.

 Bir PDB dosyası yüklendiğinde, dosyada depolanan adres eşlemesi etkinleştirilir. Ancak, bir istemci uygulamanın [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemini çağırarak kendi adres haritasını sağlaması gerekebilecek durumlar vardır. `set_addressMap`Yöntem başarılı olursa, istemci uygulamanın `put_addressMapEnabled` `NewVal` `TRUE` Bu adres eşlemesinin kullanımını etkinleştirmek için parametresiyle yöntemini çağırması gerekir.

 Etkin olan adres eşlemesinin geçerli durumu [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) yöntemi çağrısıyla alınabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
