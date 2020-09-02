---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810337"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir işlev için çağırma kuralını belirtir.  
  
> [!NOTE]
> Burada yalnızca en yaygın numaralandırma değerleri belgelenmiştir. Tüm sabit listesi, cvconst. h üstbilgi dosyasında bulunur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 CV_CALL_NEAR_C  
 Neredeyse sağdan sola gönderim kullanan bir işlev çağırma kuralını belirtir. Çağıran işlev, yığını temizler.  
  
 CV_CALL_NEAR_FAST  
 Kayıt ile neredeyse soldan sağa gönderim kullanan bir işlev çağırma kuralını belirtir. Çağrılan işlev, yığın temizlemek için parametre baytlarının toplamını kullanır.  
  
 CV_CALL_NEAR_STD  
 Yakın standart çağrı (sağdan sola gönderim) kullanan bir işlev çağırma kuralını belirtir.  
  
 CV_CALL_NEAR_SYS  
 Yakın sistem çağrısını kullanan bir işlev çağırma kuralını belirtir.  
  
 CV_CALL_THISCALL  
 `this`Çağrı ( `this` kayıt sırasında geçirilen işaretçi) kullanılarak işlev çağırma kuralını belirtir.  
  
 CV_CALL_CLRCALL  
 Ortak dil çalışma zamanı (CLR) tarafından kullanılan bir işlev çağırma kuralını belirtir (yönetilen kod çağırma kuralı olarak da bilinir).  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metoduna yapılan bir çağrı tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
