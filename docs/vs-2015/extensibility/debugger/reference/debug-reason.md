---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95a537c703d4afd68bb291205e0c7da8d9b8fc59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143020"
---
# <a name="debug_reason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İşlemin neden hata ayıklama için başlatıldığına ilişkin belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 DEBUG_REASON_ERROR  
 Belirli olmayan bir hata oluştu (diğer nedenlerden hiçbiri uygun olmadığında bu varsayılan koşul olarak kullanılır).  
  
 DEBUG_REASON_USER_LAUNCHED  
 İşlem kullanıcının isteğiyle başlatılmıştı.  
  
 DEBUG_REASON_USER_ATTACHED  
 Zaten çalışan işlem, Kullanıcı tarafından öğesine eklendi.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 İşlem başlatıldığı zaman otomatik olarak eklendi.  
  
 DEBUG_REASON_CAUSALITY  
 *Tam zamanında* (JIT) hata ayıklama olayı nedeniyle işlem başlatıldı.  
  
## <a name="remarks"></a>Açıklamalar  
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) yönteminden döndürüldü.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
