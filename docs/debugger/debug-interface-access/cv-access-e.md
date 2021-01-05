---
title: CV_access_e | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK 'sında üyelerin görünürlük (erişim düzeyi) kapsamını belirten CV_access_e numaralandırma türü hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b2cfea273d0b98c178c3cf9bcf3894042f760f
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728697"
---
# <a name="cv_access_e"></a>CV_access_e
Üye işlevlerinin ve değişkenlerinin görünürlük kapsamını (erişim düzeyi) belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Öğeler
CV_private üyesinin özel erişimi vardır.

CV_protected üyesinin erişimi korumalı.

CV_public üyenin ortak erişimi vardır.

## <a name="remarks"></a>Açıklamalar
`friend`Genellikle sınıfın hem özel hem de korumalı öğelerine erişimi olan üye olmayan işlevler tarafından kullanıldığından, erişim belirticisi buraya dahil edilmez. Access ile sembolleri bulmak için [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodunu kullanın `SymTagFriend` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
