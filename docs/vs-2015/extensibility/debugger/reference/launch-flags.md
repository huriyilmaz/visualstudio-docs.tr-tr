---
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f209ed773a72c3925661bd81ecfe2685408b3189
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147458"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama başlatma bayraklarını belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
typedef DWORD LAUNCH_FLAGS;  
```  
  
```csharp  
public enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
```  
  
## <a name="members"></a>Üyeler  
 LAUNCH_DEBUG  
 Hata ayıklama işlemini başlatır.  
  
 LAUNCH_NODEBUG  
 İşlemi hata ayıklamadan başlatır.  
  
 LAUNCH_ENABLE_ENC  
 KULLANıM DıŞı, KULLANMAYıN.  
  
 LAUNCH_MERGE_ENV  
 İşlemi başlatır ve ortamı Başlatan ana bilgisayarla birleştirir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerler, [Launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemine bir bağımsız değişken olarak geçirilir.  
  
 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
