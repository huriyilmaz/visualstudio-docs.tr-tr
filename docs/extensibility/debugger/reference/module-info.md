---
description: Belirli bir modülü (DLL, EXE veya derleme) açıklar.
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bcbe5e48918087f9252c26c0b8a9fc1f52eb3b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042809"
---
# <a name="module_info"></a>MODULE_INFO
Belirli bir modülü (DLL, EXE veya derleme) açıklar.

## <a name="syntax"></a>Syntax

```cpp
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
 `dwValidFields`\
 Hangi alanların doldurulması [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) bir bayrak birleşimi.

 `m_bstrName`\
 Modül adı.

 `m_bstrUrl`\
 Modül URL'si.

 `m_bstrVersion`\
 Modül sürümü.

 `m_bstrDebugMessage`\
 Modülle ilgili isteğe bağlı bir ileti, örneğin, "Semboller yüklenemiyor."

 `m_addrLoadAddress`\
 Modül yükleme adresi.

 `m_addrPreferredLoadAddress`\
 Modülün tercih edilen yük adresi.

 `m_dwSize`\
 Modül boyutu.

 `m_dwLoadOrder`\
 Modül yükleme sırası.

 `m_TimeStamp`\
 Sembol dosyasının en son değiştirilma zamanı.

 `m_bstrUrlSymbolLocation`\
 Modülde belirtilen sembol dosyasının konumu (örneğin, ". \\ ") . Bir modülün sembollerini bulmak için başlangıç konumu olarak kullanılır.

 `m_dwModuleFlags`\
 Modülden gelen [bayrakların MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) modülünü açıklayan bir numaralama.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [doldurulan GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine geçirildi.

 Bu yapı, Modüller penceresinde listelenen her **modüle karşılık** gelen bir yapıdır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
