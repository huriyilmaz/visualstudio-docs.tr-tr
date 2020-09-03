---
title: CONSTRUCTOR_ENUM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b435507c84d697ef27a2b37d6153a53dbe13cb3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206080"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Farklı Oluşturucu türlerini seçer.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Üyeler  
 crAll  
 Tüm oluşturucuları seçer.  
  
 Crstatic  
 Statik olmayan oluşturucular seçer.  
  
 crStatic  
 Statik oluşturucuları seçer.  
  
## <a name="remarks"></a>Açıklamalar  
 [Enumoluşturucular](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) yöntemine bir bağımsız değişken olarak geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
