---
description: İstemcinin göreli sanal adreslerin (RVA) hesaplanması ve kullanımını etkinleştirmesini veya devre dışı bırakmasını sağlar.
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
ms.openlocfilehash: 82cd5e7ee05c3e3ed024039f350b3a7f74b6fb9a826ac97a4d4ff0008b7cdb6e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345335"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
İstemcinin göreli sanal adreslerin (RVA) hesaplanması ve kullanımını etkinleştirmesini veya devre dışı bırakmasını sağlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametreler
 NewVal

[in] etkinleştirmek veya `TRUE` devre dışı bırakmak için olarak `FALSE` ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 DIA arabirimleri tarafından tanımlanan hata ayıklama nesnelerinin adresleri ve yürütülebilir dosyanın görüntü tabanına göre, göreli sanal adresler olarak alınabilirsiniz.

 Segmentler başlangıçta bir PDB dosyasından yüklendiğinde RVA'ların kullanımı etkinleştirilir. RVA'ların kullanımının geçerli durumunu almak için [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) yöntemini arayın.

 `put_relativeVirtualAddress` [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemine yapılan başarılı bir çağrıdan sonra RVA'ları etkinleştirmek için yönteminin çağrılmış olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
