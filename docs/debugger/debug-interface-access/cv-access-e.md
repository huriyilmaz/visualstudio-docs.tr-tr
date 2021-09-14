---
title: CV_access_e | Microsoft Docs
description: Hata ayıklama arabirimi CV_access_e SDK'sı üyelerinin görünürlük (erişim düzeyi) kapsamını belirten enumeration türü hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: f784380e1c96a28c200ee2f7ab70cfd21c40a343
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630698"
---
# <a name="cv_access_e"></a>CV_access_e
Üye işlevlerin ve değişkenlerin görünürlük kapsamını (erişim düzeyi) belirtir.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Öğeler
CV_private üyenin özel erişimi var.

CV_protected korumalı erişimi var.

CV_public üyenin genel erişimi var.

## <a name="remarks"></a>Açıklamalar
Erişim belirleyicisi genellikle sınıfın hem özel hem de korumalı öğelerine erişimi olan üye olmayan işlevler tarafından kullandığından `friend` buraya dahil değildir. Erişimi olan [sembolleri bulmak için IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) yöntemini `SymTagFriend` kullanın.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
