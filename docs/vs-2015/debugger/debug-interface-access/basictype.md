---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580843"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Simgenin temel türünü belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Öğeler  
 btNoType  
 Temel tür belirtilmedi.  
  
 btVoid  
 Temel tür bir `void` .  
  
 btChar  
 Temel tür bir `char` (C/C++ türüdür).  
  
 btWChar  
 Temel tür bir geniş (Unicode) karakterdir ( `WCHAR` ).  
  
 btInt  
 Temel tür `signed int` (C/C++ türü).  
  
 Btuınt  
 Temel tür `unsigned int` (C/C++ türü).  
  
 btFloat  
 Temel tür bir kayan noktalı sayıdır ( `FLOAT` ).  
  
 btBCD  
 Temel tür ikili kodlanmış bir Decimal ( `BCD` ).  
  
 btBool  
 Temel tür bir Boole değeri ( `BOOL` ).  
  
 btLong  
 Temel tür bir `long int` (C/C++ türüdür).  
  
 btULong  
 Temel tür bir `unsigned long int` (C/C++ türüdür).  
  
 btCurrency  
 Temel tür para birimidir.  
  
 btDate  
 Temel tür tarih/saat ( `DATE` ).  
  
 btVariant  
 Temel tür bir değişken tür yapısıdır ( `VARIANT` ).  
  
 btComplex  
 Temel tür karmaşık bir sayıdır.  
  
 btBit  
 Temel tür bir bittir.  
  
 btBSTR  
 Temel tür temel veya ikili bir dizedir ( `BSTR` ).  
  
 btHresult  
 Temel tür bir `HRESULT` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
