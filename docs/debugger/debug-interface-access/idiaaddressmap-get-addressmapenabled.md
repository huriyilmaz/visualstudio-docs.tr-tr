---
description: Belirli bir oturum için bir adres eşlemesinin yapılıp yapılmayacağını belirtir.
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a55ff89e97d1898ec2ced2b62f7cdfa5a0df817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149111"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Belirli bir oturum için bir adres eşlemesinin yapılıp yapılmayacağını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

dışı `TRUE` Adres eşlemesinin etkin olup olmadığını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yürütülebilir son işlemciler bazen yürütülebilir dosyayı güncelleştirebilir. DIA, sembollerin yeni düzene çevirisini desteklemek için bir mekanizma içerir.

 İstemci uygulamaları, [IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabiriminden [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) arabirimini alarak ve [ıdiaaddressmap:: Set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemini çağırarak ve sonra [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) yöntemine bir çağrı yaparak belirli bir oturumun adres eşlemesini ayarlayabilir. `get_addressMapEnabled`Yöntemi, yöntemini çağırma sonuçlarını döndürür `put_addressMapEnabled` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
