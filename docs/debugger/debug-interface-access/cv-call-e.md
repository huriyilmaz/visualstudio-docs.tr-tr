---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745349"
---
# <a name="cv_call_e"></a>CV_call_e
Bir işlev için çağırma kuralını belirtir.

> [!NOTE]
> Burada yalnızca en yaygın numaralandırma değerleri belgelenmiştir. Tüm sabit listesi, cvconst. h üstbilgi dosyasında bulunur.

## <a name="syntax"></a>Sözdizimi

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
CV_CALL_NEAR_C, neredeyse sağdan sola gönderim kullanan bir işlev çağırma kuralını belirtir. Çağıran işlev, yığını temizler.

CV_CALL_NEAR_FAST, kayıt ile neredeyse soldan sağa gönderim kullanan bir işlev çağırma kuralını belirtir. Çağrılan işlev, yığın temizlemek için parametre baytlarının toplamını kullanır.

CV_CALL_NEAR_STD yakın standart çağrı (sağdan sola gönderim) kullanan bir işlev çağırma kuralını belirtir.

CV_CALL_NEAR_SYS yakın sistem çağrısını kullanan bir işlev çağırma kuralını belirtir.

CV_CALL_THISCALL `this` çağrısı kullanarak bir işlev çağırma kuralını belirtir (`this` işaretçi kayıt içine geçirildi).

CV_CALL_CLRCALL, ortak dil çalışma zamanı (CLR) tarafından kullanılan bir işlev çağırma kuralını belirtir (yönetilen kod çağırma kuralı olarak da bilinir).

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) yöntemi çağrısıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
