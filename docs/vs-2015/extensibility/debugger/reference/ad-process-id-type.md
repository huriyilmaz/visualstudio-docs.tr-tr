---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153610"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısındaki BIR işlem kimliğinin nasıl yorumlanacağını belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Üyeler  
 AD_PROCESS_ID_SYSTEM  
 İşlem KIMLIĞI bir sistem tanımlayıcısıdır. `ProcessId.dwProcessId` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısının alanını kullanın.  
  
 AD_PROCESS_ID_GUID  
 İşlem KIMLIĞI bir GUID 'dir. `ProcessId.guidProcessId`Yapının alanını kullanın `AD_PROCESS_ID` .  
  
## <a name="remarks"></a>Açıklamalar  
 `ProcessIdType`Yapıda bulunan Işlem kimliği türünü tanımlamak için [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısının üyesi için kullanılır. Yapıdaki birleşimin nasıl yorumlanacağını belirler `ProcessId` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
