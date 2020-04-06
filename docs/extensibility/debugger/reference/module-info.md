---
title: MODULE_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714307"
---
# <a name="module_info"></a>MODULE_INFO
Belirli bir modülü (DLL, EXE veya montaj) açıklar.

## <a name="syntax"></a>Sözdizimi

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
 Hangi alanların [doldurulduğuna](../../../extensibility/debugger/reference/module-info-fields.md) MODULE_INFO_FIELDS numaralandırmadan gelen bayrakların birleşimi.

 `m_bstrName`\
 Modül adı.

 `m_bstrUrl`\
 Modül URL'si.

 `m_bstrVersion`\
 Modül versiyonu.

 `m_bstrDebugMessage`\
 Modül hakkında isteğe bağlı bir ileti, örneğin, "Semboller yüklenemez."

 `m_addrLoadAddress`\
 Modül yük adresi.

 `m_addrPreferredLoadAddress`\
 Modülün tercih edilen yük adresi.

 `m_dwSize`\
 Modül boyutu.

 `m_dwLoadOrder`\
 Modül yük sırası.

 `m_TimeStamp`\
 Sembol dosyasının en son değiştirilme zamanı.

 `m_bstrUrlSymbolLocation`\
 Sembol dosyasının konumu (örneğin, ".\\") modülde belirtilir. Bir modül için sembolleri bulmak için başlangıç konumu olarak kullanılır.

 `m_dwModuleFlags`\
 Modülü açıklayan [numaralandırma MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) gelen bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı doldurulduğu [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine aktarılır.

 Bu **yapı, Modüller** penceresinde listelenen her modüle karşılık gelir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
