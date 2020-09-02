---
title: Veri türü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197628"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir veri değerinin belirli kapsamını gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Öğeler  
 Dataısunknown  
 Veri simgesi belirlenemiyor.  
  
 Dataıslocal  
 Veri öğesi yerel bir değişkendir.  
  
 DataIsStaticLocal  
 Veri öğesi statik bir yerel değişkendir.  
  
 DataIsParam  
 Veri öğesi resmi bir parametredir.  
  
 DataIsObjectPtr  
 Veri öğesi bir nesne işaretçisidir ( `this` ).  
  
 Dataısfilestatic  
 Veri öğesi, dosya kapsamlı bir değişkendir.  
  
 Dataısglobal  
 Veri öğesi genel bir değişkendir.  
  
 DataIsMember  
 Veri öğesi bir nesne üye değişkenidir.  
  
 Dataısstaticmember  
 Veri öğesi bir sınıf statik değişkenidir.  
  
 DataIsConstant  
 Veri öğesi sabit bir değerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
