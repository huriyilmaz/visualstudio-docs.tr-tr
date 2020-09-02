---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b5cba13e439c69b3502b00c6ae159b6af28178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153243"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir kesme noktasının hatalı çözümlenmesi hakkında alınacak bilgileri belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Üyeler  
 PERESI_BPRESLOCATION  
 `bpResLocation` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısının (kesme noktası çözümleme konumu) alanını başlatın/kullanın.  
  
 BPERESI_PROGRAM  
 Yapının alanını başlatın/kullanın `pProgram` `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI_THREAD  
 Yapının alanını başlatın/kullanın `pThread` `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI_MESSAGE  
 Yapının alanını başlatın/kullanın `bstrMessage` `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI_TYPE  
 `dwType`Yapının (kesme noktası türü) alanını başlatın/kullanın `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI_ALLFIELDS  
 Yapının tüm alanlarını başlatın/kullanın `BP_ERROR_RESOLUTION_INFO` .  
  
## <a name="remarks"></a>Açıklamalar  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısının hangi alanlarının başlatıldığını göstermek Için [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) yöntemine bir parametre olarak geçirilir.  
  
 Bu değerler aynı zamanda yapıdaki hangi alanların `BP_ERROR_RESOLUTION_INFO` kullanıldığını ve bu yapı döndürüldüğünde geçerli olduğunu göstermek için kullanılır.  
  
 Bu değerler, bit düzeyinde birleştirilebilir `OR` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
