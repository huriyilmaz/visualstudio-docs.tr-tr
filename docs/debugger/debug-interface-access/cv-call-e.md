---
title: CV_call_e | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK'sı içinde bir işlev için çağırma kuralı belirten CV_call_e türü hakkında başvuru bilgilerini almak.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9619796bad01d9aba51026166819e5668743e02d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630692"
---
# <a name="cv_call_e"></a>CV_call_e
Bir işlev için çağırma kuralı belirtir.

> [!NOTE]
> Burada yalnızca en yaygın numaralama değerleri belgelenmiş durumdadır. Tam numaralama cvconst.h üst bilgi dosyasında mevcuttur.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Öğeler
CV_CALL_NEAR_C Sağdan sola itme kullanarak bir işlev çağırma kuralı belirtir. Çağıran işlev yığını temizler.

CV_CALL_NEAR_FAST Yazmazlarla soldan sağa yakın bir itme kullanarak bir işlev çağırma kuralı belirtir. Çağrılı işlev, yığını temizlemek için parametre baytlarının toplamını kullanır.

CV_CALL_NEAR_STD Yakın standart bir çağrı (sağdan sola itme) kullanan bir işlev çağırma kuralı belirtir.

CV_CALL_NEAR_SYS Yakın sistem çağrısı kullanan bir işlev çağırma kuralı belirtir.

CV_CALL_THISCALL Çağrısı (yazmaçta geçirilen `this` işaretçi) kullanarak `this` bir işlev çağırma kuralı belirtir.

CV_CALL_CLRCALL Ortak Dil Çalışma Zamanı (CLR) (yönetilen kod çağırma kuralı olarak da bilinir) tarafından kullanılan bir işlev çağırma kuralı belirtir.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_callingConvention yöntemine yapılan bir çağrıyla](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
