---
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d733a51bd599b85dcc6d1121b8d21e1a687a351
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745038"
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

'ndaki Etkinleştirmek için `TRUE` veya devre dışı bırakmak için `FALSE`.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 DIA arabirimleri tarafından tanımlanan hata ayıklama nesnelerinin adresleri ve yürütülebilir dosyanın görüntü tabanına göreli olarak, göreli sanal adresler olarak alınabilir.

 RVA kullanımı, kesimler başlangıçta bir PDB dosyasından yüklendiğinde etkinleştirilir. RVA öğesinin geçerli durumunu almak için [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemini çağırın.

 [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi için başarılı bir çağrıdan yeni görüntü üstbilgileri kurulduktan sonra RVA etkinleştirmek için `put_relativeVirtualAddress` yöntemi çağrılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)