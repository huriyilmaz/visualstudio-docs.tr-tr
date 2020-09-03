---
title: 'IDiaAddressMap:: get_relativeVirtualAddressEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 287f076e4ae38f26cec6046896d978319c872148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468583"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Göreli sanal adreslerin (RVA) hesaplanması ve kullanılması etkinleştirilip etkinleştirilmeyeceğini belirtir.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

dışı `TRUE` RVA hesaplamasının etkin olup olmadığını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 RVA, kesimler başlangıçta bir PDB dosyasından yüklenirse etkinleştirilir. RVA kullanımı [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) yöntemi çağırarak geçici olarak devre dışı bırakılabilir.

 Ayrıca, yeni görüntü üstbilgileri, [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi çağırarak ve ardından `put_relativeVirtualAddressEnabled` yeni görüntü üst bilgilerini kullanarak RVA kullanımını etkinleştirmek üzere yöntemine yapılan bir çağrı tarafından oluşturulabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)