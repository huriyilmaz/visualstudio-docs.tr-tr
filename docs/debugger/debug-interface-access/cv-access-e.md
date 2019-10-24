---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745363"
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

CV_protected üyesinin korumalı erişimi vardır.

CV_public üyesinin ortak erişimi vardır.

## <a name="remarks"></a>Açıklamalar
@No__t_0 erişim belirticisi, genellikle sınıfın hem özel hem de korumalı öğelerine erişimi olan üye olmayan işlevler tarafından kullanıldığından, burada dahil değildir. @No__t_1 erişimi olan sembolleri bulmak için [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) yöntemini kullanın.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
