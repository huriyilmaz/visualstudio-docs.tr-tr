---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04a8756fd7eb2a4b938ebcd2d5f4754509b704e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205212"
---
# <a name="module_info"></a>MODULE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirli bir modülü (DLL, EXE veya derleme) açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```csharp  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## <a name="members"></a>Üyeler  
 dwValidFields  
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.  
  
 m_bstrName  
 Modül adı.  
  
 m_bstrUrl  
 Modül URL 'SI.  
  
 m_bstrVersion  
 Modül sürümü.  
  
 m_bstrDebugMessage  
 Modülle ilgili isteğe bağlı bir ileti, örneğin "semboller yüklenemiyor".  
  
 m_addrLoadAddress  
 Modül yükleme adresi.  
  
 m_addrPreferredLoadAddress  
 Modülün tercih edilen yükleme adresi.  
  
 m_dwSize  
 Modül boyutu.  
  
 m_dwLoadOrder  
 Modül yükleme sırası.  
  
 m_TimeStamp  
 Sembol dosyasının son değiştirilme zamanı.  
  
 m_bstrUrlSymbolLocation  
 Modülde belirtilen sembol dosyasının konumu (örneğin, ". \\ "). Bir modülün sembollerini bulmak için başlangıç konumu olarak kullanılır.  
  
 m_dwModuleFlags  
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) numaralandırmasından modülü tanımlayan bayrakların birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, doldurulduğu [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine geçirilir.  
  
 Bu yapı, **modüller** penceresinde listelenen her modüle karşılık gelir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
