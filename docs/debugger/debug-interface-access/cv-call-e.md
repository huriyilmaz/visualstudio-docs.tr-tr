---
title: CV_call_e | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK 'sında bir işlevin çağırma kuralını belirten CV_call_e numaralandırma türü hakkında başvuru bilgileri alın.
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
ms.openlocfilehash: b6a52467ce6436703387df6055ae8d65daca56181f2dbad8c7f47929e35020b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345733"
---
# <a name="cv_call_e"></a>CV_call_e
Bir işlev için çağırma kuralını belirtir.

> [!NOTE]
> Burada yalnızca en yaygın numaralandırma değerleri belgelenmiştir. Tüm sabit listesi, cvconst. h üstbilgi dosyasında bulunur.

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
CV_CALL_NEAR_C, neredeyse sağdan sola gönderim kullanan bir işlev çağırma kuralını belirtir. Çağıran işlev, yığını temizler.

CV_CALL_NEAR_FAST, kayıt ile neredeyse soldan sağa gönderim kullanan bir işlev çağırma kuralını belirtir. Çağrılan işlev, yığın temizlemek için parametre baytlarının toplamını kullanır.

CV_CALL_NEAR_STD, neredeyse standart bir çağrı (sağdan sola gönderim) kullanan bir işlev çağırma kuralını belirtir.

CV_CALL_NEAR_SYS, yakın sistem çağrısını kullanan bir işlev çağırma kuralını belirtir.

CV_CALL_THISCALL, çağrı kullanarak bir işlev çağırma kuralını belirtir `this` ( `this` kayıt sırasında geçirilen işaretçi).

CV_CALL_CLRCALL, ortak dil çalışma zamanı (CLR) tarafından kullanılan bir işlev çağırma kuralını belirtir (yönetilen kod çağırma kuralı olarak da bilinir).

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metoduna yapılan bir çağrı tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
