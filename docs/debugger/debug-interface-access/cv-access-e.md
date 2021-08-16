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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 98803034210b9897d6d40a2378791c8ce5385110589b05dd602fd27159e26059
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326580"
---
# <a name="cv_access_e"></a>CV_access_e
Üye işlevlerinin ve değişkenlerinin görünürlük kapsamını (erişim düzeyi) belirtir.

## <a name="syntax"></a>Syntax

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
