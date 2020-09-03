---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205014"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir işlem hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Üyeler  
 Alanlar  
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.  
  
 bstrFileName  
 İşlemin tam yol adı. Parametresiyle [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodunu çağırmaya eşdeğerdir `GN_FILENAME` .  
  
 bstrBaseName  
 İşlemin dosya adı ve uzantısı. `IDebugProcess2::Getname`Yöntemi parametresiyle çağırma ile eşdeğerdir `GN_BASENAME` .  
  
 bstrTitle  
 Bir varsa, işlemin başlığı. `IDebugProcess2::Getname`Yöntemi parametresiyle çağırma ile eşdeğerdir `GN_TITLE` .  
  
 Işlem  
 İşlemi tanımlayan [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısı. [Getphysicalprocessıd](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) yöntemini çağırmaya eşdeğerdir.  
  
 Dwsessionıd  
 Bu işlemin üzerinde çalıştığı hata ayıklama oturumunun tanımlayıcısı.  
  
 Bstrattachedoturumadı  
 Eklenen oturum adı. [Getattachedoturumadı](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) yöntemini çağırmaya eşdeğerdir.  
  
 CreationTime  
 İşlemin oluşturulduğu zaman.  
  
 Bayraklar  
 İşlemin özelliklerini belirten [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Numaralandırmadaki bayrakların birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, doldurulduğu [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [Getphysicalprocessıd](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
