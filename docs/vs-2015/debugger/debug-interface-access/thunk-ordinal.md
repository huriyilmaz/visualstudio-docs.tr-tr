---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576414"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dönüştürücü türlerini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Öğeler  
 THUNK_ORDINAL_NOTYPE  
 Standart dönüştürücü.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Bir `this` ayarlanıcısı dönüştürücü.  
  
 THUNK_ORDINAL_VCALL  
 Sanal Çağrı dönüştürücü.  
  
 THUNK_ORDINAL_PCODE  
 P kodu dönüştürücü.  
  
 THUNK_ORDINAL_LOAD  
 Yük dönüştürücü gecikmesi.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Artımlı trampoline dönüştürücü (bir trampoline dönüştürücü, bir bellek alanından diğerine yapılan çağrıları sıçramalar için kullanılır).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Dal noktası trampoline dönüştürücü.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler, [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metoduna yapılan çağrıdan döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
