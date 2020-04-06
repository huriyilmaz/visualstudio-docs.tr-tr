---
title: MODULE_INFO_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714325"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Hata ayıklama modülü bilgileri için bayrakları belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Alanlar
 `MIF_NONE`\
 Yapıdaki alanların hiçbirini başlatma/kullanma.

 `MIF_NAME`\
 `m_bstrName` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısındaki alanı başlatma/kullanma.

 `MIF_URL`\
 `MODULE_INFO` Yapıdaki `m_bstrUrl` alanı başlatma/kullanma.

 `MIF_VERSION`\
 `MODULE_INFO` Yapıdaki `m_bstrVersion` alanı başlatma/kullanma.

 `MIF_DEBUGMESSAGE`\
 `MODULE_INFO` Yapıdaki `m_bstrDebugMessage` alanı başlatma/kullanma.

 `MIF_LOADADDRESS`\
 `MODULE_INFO` Yapıdaki `m_addrLoadAddress` alanı başlatma/kullanma.

 `MIF_PREFFEREDADDRESS`\
 `MODULE_INFO` Yapıdaki `m_addrPreferredLoadAddress` alanı başlatma/kullanma.

 `MIF_SIZE`\
 `MODULE_INFO` Yapıdaki `m_dwSize` alanı başlatma/kullanma.

 `MIF_LOADORDER`\
 `MODULE_INFO` Yapıdaki `m_dwLoadOrder` alanı başlatma/kullanma.

 `MIF_TIMESTAMP`\
 `MODULE_INFO` Yapıdaki `m_TimeStamp` alanı başlatma/kullanma.

 `MIF_URLSYMBOLLOCATION`\
 `MODULE_INFO` Yapıdaki `m_bstrUrlSymbolLocation` alanı başlatma/kullanma.

 `MIF_FLAGS`\
 `MODULE_INFO` Yapıdaki `m_dwModuleFlags` alanı başlatma/kullanma.

 `MIF_ALLFIELDS`\
 Yapıdaki tüm alanların başlatılması/kullanılması. `MODULE_INFO`

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısının hangi alanlarının başharfe başlatılanolacağını belirtmek için [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) yöntemine bir bağımsız değişken olarak aktarılır.

 Bu değerler `MODULE_INFO` yapıda hangi alanların kullanıldığını ve geçerli olduğunu belirtmek için de kullanılır.

 Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
