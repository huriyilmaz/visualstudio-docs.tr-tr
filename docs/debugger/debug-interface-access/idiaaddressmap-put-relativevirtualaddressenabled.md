---
description: İstemcinin, göreli sanal adreslerin (RVA) hesaplanmasını ve kullanımını etkinleştirmesine veya devre dışı bırakmasına izin verir.
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9cfb2e9b3b77adb5e0b16b896100b5b9eab04596
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630530"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
İstemcinin, göreli sanal adreslerin (RVA) hesaplanmasını ve kullanımını etkinleştirmesine veya devre dışı bırakmasına izin verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

'ndaki `TRUE` Öğesini etkinleştirmek veya `FALSE` devre dışı bırakmak için olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 DIA arabirimleri tarafından tanımlanan hata ayıklama nesnelerinin adresleri ve yürütülebilir dosyanın görüntü tabanına göreli olarak, göreli sanal adresler olarak alınabilir.

 RVA kullanımı, kesimler başlangıçta bir PDB dosyasından yüklendiğinde etkinleştirilir. RVA öğesinin geçerli durumunu almak için [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemini çağırın.

 `put_relativeVirtualAddress` [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi için başarılı bir çağrıdan sonra RVA etkinleştirmek üzere yöntemi çağrılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
