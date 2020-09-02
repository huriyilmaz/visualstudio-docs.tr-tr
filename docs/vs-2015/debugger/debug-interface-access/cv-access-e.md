---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164379"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Üye işlevlerinin ve değişkenlerinin görünürlük kapsamını (erişim düzeyi) belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Öğeler  
 CV_private  
 Üyenin özel erişimi vardır.  
  
 CV_protected  
 Üyenin erişimi korumalı.  
  
 CV_public  
 Üyenin ortak erişimi vardır.  
  
## <a name="remarks"></a>Açıklamalar  
 `friend`Genellikle sınıfın hem özel hem de korumalı öğelerine erişimi olan üye olmayan işlevler tarafından kullanıldığından, erişim belirticisi buraya dahil edilmez. Access ile sembolleri bulmak için [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodunu kullanın `SymTagFriend` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
